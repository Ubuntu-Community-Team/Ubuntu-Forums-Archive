---
title: "Beryl completely distorts my screen"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Nate7679 on 2007-03-22
After I run beryl, everything turns bright green the screen divides into what looks like my two workspaces. Anything that moves on screen (such as menus) will stay there. Its tough to describe but it is impossible to use, and I'm barely able to log out so that I can restart ubuntu. I wish I had a screenshot but i'm not sure how to get one except for taking a picture with a camera.

I installed beryl using this guide: 

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX#Note](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX#Note)

When I log in after I log out from having this problem, Bug Buddy pops up with this error report:

0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb73166cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e391b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb72b1770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb72b2ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7483122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7483159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0x0805d500 in main ()

Thread 2 (Thread -1233851488 (LWP 5664)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb734b803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb747d813 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb747db89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb7a177e0 in link_set_io_thread () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#5  0xb749838f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb70bf504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7  0xb735551e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1232554320 (LWP 5641)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb73166cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb7e391b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb72b1770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb72b2ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7483122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7483159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0x0805d500 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


I'm running this on a laptop with 1gb of ram, 2gb swap, and an Nvidia Geforce Go 6400 with its drivers installed. I know that this isn't a setup that can run beryl in its full glory, but I've heard of it running on much cheaper systems, so I don't think my hardware is the problem.

Another thing, I only have this problem when I run "Beryl" or "Beryl Manager". However, "Beryl Settings Manager" runs fine.

I hope I've provided enough information. I understand that it could be tough to diagnose the problem without a picture of what it looks like.

Thanks for your help.

---

### Post by brandoncolorado on 2007-03-22
Sorry, not sure if this is 100% relevant, but it seem similar.

[http://ubuntuforums.org/showthread.php?p=2318904](http://ubuntuforums.org/showthread.php?p=2318904)

Reinstall Ubuntu?

---

### Post by NikoC on 2007-03-22
I don't know if this helps, but last time I read about a green screen in combination with it was an incorrect screen depth setting...
Just to make sure do (assuming that you are using gnome; otherwise replace gedit with kate or nano):

sudo gedit /etc/X11/xorg.conf

Find the Section "Screen" in this file and make sure DefaultDepth is set to 24! If it isn't, do so, save the file and restart X.

---

### Post by Nate7679 on 2007-03-22
I thought that the guide I used would install it for nvidia but it didn't. I'm now using this guide:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Installing_the_nVIDIA_Beta_Driver](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Installing_the_nVIDIA_Beta_Driver)

with the Nvidia beta driver. I assume that I'll need to uninstall the nvidia driver I already have installed for this to work, how should I do that?

---

### Post by NikoC on 2007-03-22
In a terminal type:

sudo apt-get remove --purge nvidia-glx nvidia-kernel-common linux-restricted-modules-$(uname -r)

This command will remove all nvidia-related packages and purge them as well!

If you want to reboot for some reason without installing new drivers make sure you do a:

sudo gedit /etc/X11/xorg.conf

Find the Section "Device" and replace Driver "nvidia"  with Driver "nv" and save the file.
Otherwise your x-server will be looking for nvidia kernel modules that you had removed in the previous line I posted.

You then can make a clean install as instructed on the link you've posted.

---

