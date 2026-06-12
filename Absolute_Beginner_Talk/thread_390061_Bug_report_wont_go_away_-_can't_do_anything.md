---
title: "Bug report wont go away - can't do anything"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by toscy on 2007-03-21
Hi,

I was just trying to mount an iso with gisomount and the bug report tool came up. Whenever I try and close it it comes back up again, maybe reporting the same bug than a bug with the bug reporter.

So I have the 3 top left things (applications, places and administration) but my tray bar has gone as well as the bottom bar. I can't access the top left 3 things, nothing happens when I click on them. However, I can acess things normally with that annoying bug report in the way by the shortcuts on my desktop. 

Where can I acess firefox from?

I've looked in my username directory with ctrl+h and gone into the mozilla folder but I can't find a .exe (I know linux doesn't use .exe, what does it use?). This way I can atleast get on this forum easier.

Secondly, how do I fix this problem? 

I'll post the bug report when I can access firefox as it will be alot easier.

Thanks for reading this and for any responses and sorry for my bad explanation. I can give any extra information that you may need. 

Thank you.

---

### Post by toscy on 2007-03-21
Ok, I've managed to open firefox from a .html file I found on my hd. Here it is.

Memory status: size: 57745408 vsize: 0 resident: 57745408 share: 0 rss: 17301504 rss_rlim: 0
CPU usage: start_time: 1174502262 rtime: 0 utime: 60 stime: 0 cutime:57 cstime: 0 timeout: 3 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225222480 (LWP 5756)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7640323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f381b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7528770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7529ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7744122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7744159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb77441d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b93d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b93dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b8f591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb7739aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb773b802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb773e7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb773eb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b3d574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225222480 (LWP 5756)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7640323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f381b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7528770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7529ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7744122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7744159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb77441d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b93d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b93dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b8f591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb7739aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb773b802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb773e7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb773eb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b3d574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by belikralj on 2007-03-21
can you try this command in a terminal (if you can't get to a terminal use <alt>+F2 and select option run in terminal):

ps -e -t tty7

then find the name of the proces of the bugreport and use

kill <process id of the bug report>

and then you can post it here if kill doesn't work

---

### Post by belikralj on 2007-03-21
sorry didn't mean to sound rude (re-reading the post I see I did sound a little overbearing), I didn't see your last post before posting my answer. If only bug-report is the problem than you can kill it the way I suggested and then try to get your system back up but if it's something else this may not work

---

### Post by belikralj on 2007-03-21
Ok, I don't know what's going on, I can only guess but guessing is not what would help you :(. Hopefully some of the more experienced guys here will be able to help.

---

### Post by fakie_flip on 2007-03-21
Have you tried restarting x using control alt and backspace? The bug report thing will be gone after that.

---

### Post by fakie_flip on 2007-03-21
There is a command to mount iso files. You do not need gisomount.

First create an empty directory that you want to mount file.iso or use /mnt.

```
sudo mount -o loop /home/user/file.iso /mnt
```

Now you can do this to see if it worked.

```
ls /mnt
```

---

### Post by toscy on 2007-03-21
Belikralj, thanks alot for attempting to help me, it's appreciated! I haven't been able to get to the terminal though as alt+f2 doesn't do anything. I'm afraid I'm not experienced enough to know any other way or where it is (and a lot of other things too) are placed in the file system.

Fakie_flip, I've restarted my computer twice now so I assume that's the same as doing what you said? I'll try anyway (Edit: It didn't work) . As for mounting via the command line, I knew you could do it one of those ways (I've seen several scripts and variants of what you wrote) but I thought by getting a program it would be easier and prevent me googling a howto in the future. Thanks for your help too. In the future I will deffinately use command line when this is hopefully fixed.

Any other suggestions? :( 

Thanks!

---

### Post by toscy on 2007-03-21
Belikralj, I managed to get into the terminal and did what you said but it still keeps coming back up. 

Sorry, I probably didn't make it clear what I was trying to say. I can close the bug report (either with the x, send or close) but about two seconds after it comes back up again with the same bug it's reporting again probably indicating quite a serious problem. :( 

In the two seconds from when I close it to when it comes back up, it tries to load my desktop (or however you put it) again but then gets interrupted. So sometimes I can't see my bottom bar, sometimes I can and sometimes the top bar doesn't get to loading as transparent etc.

---

### Post by belikralj on 2007-03-21
Well, I'm not sure what the problem is but you also have the option to go to 6 other terminals. Press <ctrl>+<alt>+F1 or <ctrl>+<alt>+F2 or <ctrl>+<alt>+F3 .... to <ctrl>+<alt>+F6 and <ctrl>+<alt>+F7 is your X terminal in which you have the bug report. But from those shells you can't run firefox from them. I'm not sure where the problem lies but it appears to me as if /usr/lib/libglib-2.0.so.0 and the other libraries may not be functioning properly. I'm not farmiliar with either gisomout or bug report tool so I don't know wether the command gisomount messes with the libraries. You could try reinstalling those libraryes again. Can you get to synaptic some way? If you have the LiveCD someone more literate with the Command line could halp you more probably. I would try looking in Synaptic if you can for packages that are broken and reinstalling them or at least the ones mentioned in your second post. I really don't know what else to try :|. From the live cd you could try the safe mode and it should give you some options but I don't know how to reinstall things on the hard disc when booted of the LiveCD. I could give you some help moving your files using the LiveCD and mounting your hard disc but I'm not sure how else to help. You could back up your stuff and reinstall as a last resort but let's postpone that for now. Try the System -> Administration -> Synaptic Package Manager

I would like to ask the other members wheter you can repair X from the LiveCD or at least reset the default settings somehow?

Where did you try to mount the iso?

---

### Post by toscy on 2007-03-21
Ok, once again thanks for the help. I didn't know about all these terminals. 

For the moment I'm going to try and open synaptic package manager somehow. I'm not sure what I'm hoping it will inform me of broken packages with an option to fix but probably not.

I don't remember exactly what happened before this whole thing happened but...

I tried to mount the iso with the command line first. It gave an example to mount to hda 1 I think which I copied and pasted stupidly. I was thinking it was like cd1 or something...but I don't even think it worked as I think the console came up with an error...possibly...

Nothing happened then anyway, so I moved onto gisomount which I found in synaptic. I tried to mount an .iso and clicked mount and it said it wasn't an .iso (which it was), so I then tried another and it worked. I tried the first one again and the same error came up along with the bug report. That's when it all started. Probably useless information but that's all I can remember (bad memory lol).

Thanks for keeping on trying to help me belikralj!

---

### Post by belikralj on 2007-03-21
In synaptic you could try searching for those libraries that were mentioned in that post of yours and reinstall them, like /usr/lib/libglib-2.0.so.0 try looking just for the last part libglib-2.0.so.0 in synaptic

---

### Post by toscy on 2007-03-21
Is the command to open synaptic from the terminal "gksudo synaptic"? I read that somewhere but when I try and use it with any terminal but f7 it says it cannot open the display which figures.

I'm trying to open the terminal in f7 like I once did before but I'm having difficulty again. 

Thanks for the addition, I'll be sure to do that once I get into synaptic.

EDIT: I just got into synaptic. It doesn't report any broken packages after I checked. I searched for libglib but there was no libglib-2.0.so.0. The ones that I already had installed I checked to reinstall. I assume you got libglib-2.0.so.0. from the bug report I posted. But why if I don't have one does it show in the bug report I wonder (Edit: it shows in the file system). I also checked a complete removal of gisomount. I applied all these by the way.

If my libglib-2.0.so.0 is the problem could I not just get this file from someone else? And there shouldn't be any risk because it's already broken, right?

---

### Post by toscy on 2007-03-22
Sorry to bump this but it's been 12 hours and at first glance it may look like the problem is solved when it's not :( 

My Linux is screwed!

---

### Post by toscy on 2007-03-22
Wow, it now seems to be fixed! :confused: 

I've left my computer for half an hour, came back and there is now a bomb icon stating that it has a crash report detected in the system tray. So the system tray is back and everything is working again! :) 

It's weird though because I left my computer several times yesterday for longer times than this and it didn't fix.

Thanks for your help guys.

---

### Post by fakie_flip on 2007-03-26
What about using xkill to get rid of the bug report? You could push alt+f2 and type in xkill in the run box or type xkill in a gnome-terminal/xterm. If you are not able to do either of those, then you could push control alt f1 to switch to a linux console tty0, login, and type the command "DISPLAY=:0 xkill" without quotes. Then switch back to the console that is running the graphics server x, control alt f7. xkill will give your mouse cursor a skull and bones, so that you can click on an application to kill it immediately. If that does not work, try uninstalling the bug report program or disabling its service.

---

