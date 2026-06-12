---
title: "Problem with updating, starting terminal and grafics"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by naycon on 2007-06-10
I just installed ubuntu (and linux) for the first time. I've been using solaris occationaly in school, but decided I would give linux a try when I needed to format my computer. So here I am, with a fresh installation of ubuntu (coexcisting with windows xp) on my Dell Latitude D800 (containing a nvidia gforce 4200 ti go card).

Now, here's my list of problems:

Updateing my system:
Update manager will only refresh the update list when I press install updates. I found this bugreport: 
[https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/51419](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/51419)
which seem to say mainly that this is a problem experienced pre feisty for Italian users and there's some sort of fix there. To begin with, I don't know how to use that fix, or even if it is a good idea since the fix is related to another language and another version of ubuntu. Should I try it?
I used the sudo apt-get upgrade to update my system, but it would be nice if the update manager would work. 

Add/remove software:
Now, I don't know if these problems might be related, but when trying to install/remove applications I ran into a similar problem. When clicking "apply" after selecting a new application to install, "add/remove" will only reload the list of available applications. So, I tried to use the synaptic software manager instead. 

Synaptic Software Manager:
Now, here I ran into another problem. After entering my password into the box, nothing happens. No window, no bar in the bottom panel, nothing. I don't know, but this might be related to my next problem...

Starting a terminal:
When trying to start a terminal, nothing happens. There's a bar in the bottom panel, saying "starting terminal" but after awhile it just dissappears. Now, this seem to be some sort of bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232)
Now, I tried both the mentioned fixes in there and none of them worked (if I understood it right, I wasn't suppose to do anything but sudo nano edit the xorg.conf file in /etc/X11/ with the suggested lines and reboot). So how did I use the apt-get command? I ran xterm through the run-panel. As I said, maybe this might be related to the synaptic software manager. I hooked on that trail and thought it might have something to do with nvidia drivers and stuff to do.

Nvidia drivers:
So I thought I might have to update the nvidia drivers somehow. But I haven't been able to figure out exactly how to update the drivers. I found some posts on the topic:
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)  (see section 2)
but it speak about scripts and I don't realy get what I'm supposed to do. I might try this out if I can figure out what I'm supposed to do. 
Also, when trying to access the desktop effects menu I'm asked to install the nvidia 3D drivers something and clicking yes there imidiately gives me a new popup saying I have to reboot to enable the new drivers. But after rebooting and clicking the desktop effects menu, I'm asked to update the drivers again. Guess it's related to the problem with updating the system or adding/removing software.

Starting Gaim:
Gaim is having a similar problem to the terminal. I can see a bar in the bottom panel saying "starting gaim", but then it dissapears. Starting gaim in debug mode through xterm gives the following message:
root@Naycon:/home/naycon# gaim -d
dbus: Failed to get connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
plugins: probing /usr/lib/gaim/statenotify.so
plugins: probing /usr/lib/gaim/libqq.so
plugins: probing /usr/lib/gaim/liboscar.so
plugins: /usr/lib/gaim/liboscar.so is not usable because the 'gaim_init_plugin' symbol could not be found.  Does the plugin call the GAIM_INIT_PLUGIN() macro?
plugins: probing /usr/lib/gaim/gevolution.so
plugins: probing /usr/lib/gaim/libzephyr.so
plugins: /usr/lib/gaim/libzephyr.so is not loadable: libzephyr.so.3: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/libnovell.so
plugins: probing /usr/lib/gaim/history.so
plugins: probing /usr/lib/gaim/dbus-example.so
plugins: probing /usr/lib/gaim/markerline.so
plugins: probing /usr/lib/gaim/s.so
plugins: /usr/lib/gaim/s.so is not loadable: /usr/lib/libpanelw.so.5: invalid ELF header
plugins: probing /usr/lib/gaim/ssl-nss.so
met.
plugins: probing /usr/lib/gaim/convcolors.so
plugins: probing /usr/lib/gaim/newline.so
plugins: probing /usr/lib/gaim/timestamp_format.so
plugins: probing /usr/lib/gaim/libicq.so
plugins: probing /usr/lib/gaim/musicmessaging.so
plugins: probing /usr/lib/gaim/offlinemsg.so
plugins: probing /usr/lib/gaim/gntgf.so
plugins: /usr/lib/gaim/gntgf.so is not loadable: /usr/lib/libpanelw.so.5: invalid ELF header
plugins: probing /usr/lib/gaim/autoaccept.so
plugins: probing /usr/lib/gaim/libirc.so
plugins: probing /usr/lib/gaim/perl.so
Segmentation fault (core dumped)
root@Naycon:/home/naycon#

So I thought I would try out a different IM application, but I haven't figured out how to use sudo apt-get install to add one. I guess I somehow should specify what I want to install, but simply adding the name of the app didn't work.


As you can see I'm in pretty much trouble here, since it seem like two or three bugs or problems seem to connect eachother into a mess. Please help me sort out this mess, ubuntu looks promising, but I can't use it with "half" the OS not working as intended.

Thanks in advance and have a good day!
/Naycon

---

