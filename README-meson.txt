Build on Amlogic GX mainline
############################

Place framebuffer libMali.so in /usr/lib/mali
Add it's symlinks

Add an entry in ld.so.conf

Run ldconfig

Configure with :
./configure --without-x --enable-video-opengles --disable-video-opengl --enable-video-mali --disable-video-x11 --disable-video-wayland

Make & Install :
make install

Build tests :
cd test/
SDL_LIBS="-L/usr/local/lib -Wl,-rpath,/usr/local/lib -lSDL2 -L/usr/lib/mali" ./configure --without-x
./testgles
./testgles2

You should see something on the FB.

To detach the fbcon :
echo 0 > /sys/class/vtconsole/vtcon1/bind
