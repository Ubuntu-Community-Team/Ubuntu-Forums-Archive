---
title: "&quot;Gtk - Warning: This process is currently running setuid or setgid.&quot;"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Clodd on 2008-04-05
Hi, I just rebooted my computer and I can't login, I'm getting a:

>  (process:6112): Gtk-WARNING **: This process is currently running setuid or setgid.


This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:6116): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)


Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
x-session-manager: error while loading shared libraries /usr/lib/libconf-2.so.4: invalid ELF header

Would anyone please be able to help me get back on, I'm fairly new to this so I'm not sure where I go from here.

Thanks,

---

### Post by Amarsingh0793 on 2008-04-05
Have you tried Recovery mode yet?

---

### Post by Amarsingh0793 on 2008-04-05
Look at this thread: [http://ubuntuforums.org/showthread.php?t=130892](http://ubuntuforums.org/showthread.php?t=130892)

---

### Post by Clodd on 2008-04-05
Hi, thanks for the reply. I assumed I'd have to go into recovery mode, but I'm new to Linux so I wasn't sure what to do once I'm there, I couldn't quite understand the link you gave me.

---

### Post by Amarsingh0793 on 2008-04-05
This problem means something is wrong with one of the files in /etc/... (I forgot it :mad:). I will get back to you when I remember where. Remember in the meantime, you can go to launchpad and file a bug there, as Launchpad is looked at by developers who can fix this. 

Hope this helps :)

---

### Post by Clodd on 2008-04-05
Thanks for the explanation, I'll head to launchpad and check it out =)

---

### Post by bududu on 2008-04-06
I have the same issue. I installed kvpnc, openvpn and network-manager yesterday and now I can't login to my usual gnome session due to problems that are described in this topic.
I've removed all these applications but It didn't help.

Please, advice me how can I know the name of the process in these messages:

(process:7299): Gtk-WARNING **: This process is currently running setuid or setgid.


I see that the problem probably before 

/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: Executing /usr/bin/gnome-session failed, will try to run x-terminal-emulator

but I amn't sure.

Please, advice me, where can I look for source of this issue? I amn't new to linux, but I used to use console :) and know almost nothing about gnome, gdm, etc..
How can I switch debug on to see what is going on with gnome-session?

Thank you.

---

### Post by Amarsingh0793 on 2008-04-06
Can both of you please tell me what version of ubuntu you are using?

---

### Post by bududu on 2008-04-06
Latest Ubuntu 7.10, x86 with latest updates.

---

### Post by Amarsingh0793 on 2008-04-06
You should also try Launchpad as this seems like a bug which the developers should take a look at

---

