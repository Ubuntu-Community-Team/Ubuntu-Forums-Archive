---
title: "&quot;Your session only lasted less than 10 seconds&quot; Fluxbox Feisty.."
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by BOBSONATOR on 2007-04-30
Everything was working perfect, then all of a sudden i log in and i get this error.

This is my fluxbox startup

```
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.
fbsetbg -l
gnome-volume-manager &
xscreensaver -nosplash &

```

Thanks in advance!

---

### Post by riminicat on 2007-04-30
Hey I got this with enlightenment too, what happens when you switch sessions?

---

### Post by bapoumba on 2007-04-30
You probably have lost permission on your .ICEAuthority file.
```
~$ ls -l .ICEauthority
-rw------- 1 bapoumba bapoumba 644 2007-04-30 09:31 .ICEauthority
```
If it shows this file belongs to root, login recovery mode (no X session running, and careful, you'll be root) and delete or rename the file and reboot:
```
~# mv .ICEAuthority .ICEAuthority_bak
~# reboot
```
A new one will be automatically created.

---

### Post by BOBSONATOR on 2007-04-30
BTW: im using fluxbox, and i log into gnome fine.

and that didint work^

---

### Post by kerry_s on 2007-04-30
You forgot the & after fbsetbg -l, it should be

fbsetbg -l &

but you should put that in the init file.
look for
session.screen0.rootCommand:
and change to
session.screen0.rootCommand:	fbsetbg -l

---

### Post by bapoumba on 2007-04-30
Hum, not sure I can help you.
The 10 sec message is usually an X session message, do you have anything in your .xsession-errors that could help you pin a problem ?

---

### Post by kerry_s on 2007-04-30
> **bapoumba said:**
> Hum, not sure I can help you.
The 10 sec message is usually an X session message, do you have anything in your .xsession-errors that could help you pin a problem ?

Yeah if you forget then & it will stop with a session error.

---

### Post by bapoumba on 2007-04-30
> **kerry_s said:**
> Yeah if you forget then & it will stop with a session error.
Sorry kerry_s, I posted after you, but I had my browser opened on this thread for quite a while, looking around. I should have reloaded before posting, or deleted my post ;)

---

### Post by kerry_s on 2007-04-30
> **bapoumba said:**
> Sorry kerry_s, I posted after you, but I had my browser opened on this thread for quite a while, looking around. I should have reloaded before posting, or deleted my post ;)

No need be sorry, i do that all the time. Your help is greatly appreciated, i just had surgery and the meds leave me foggy in the head and tired most of the time. I have been helping less and less because i can't think straight most of the time.

---

### Post by bapoumba on 2007-04-30
> **kerry_s said:**
> No need be sorry, i do that all the time. Your help is greatly appreciated, i just had surgery and the meds leave me foggy in the head and tired most of the time. I have been helping less and less because i can't think straight most of the time.
Best wishes to you, kerry_s, thanks for your presence on the forums. Hope you'll get better soon.
Cheers,
bapoumba.

---

### Post by ray007 on 2007-05-02
I have the same problem with standard gnome session (with beryl) and gnome fail-safe session.
Logging in with fail-safe terminal and starting a gnome-session from there **partly** works.

Here the .xsession-errors:
------------------------------------------------------------------------------------------------
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ray"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/doriath:/tmp/.ICE-unix/5795
*** glibc detected *** x-session-manager: malloc(): memory corruption: 0x0821cbe8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7629ef3]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb762b60e]
/usr/lib/libICE.so.6[0xb7ea65d9]
/usr/lib/libICE.so.6(_IceTransAccept+0x19)[0xb7ea5f19]
/usr/lib/libICE.so.6(IceAcceptConnection+0x28)[0xb7ea2c38]
x-session-manager[0x80556fc]
/usr/lib/libglib-2.0.so.0[0xb776340d]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7739df2]
/usr/lib/libglib-2.0.so.0[0xb773cdcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb773d179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c71044]
x-session-manager(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75d7ebc]
x-session-manager[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 03:06 34403      /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 03:06 34403      /usr/bin/gnome-session
08069000-08259000 rw-p 08069000 00:00 0          [heap]

[---------- big part of memory map cut -----------------]

b7f87000-b7f89000 rw-p b7f87000 00:00 0 
b7f89000-b7fa2000 r-xp 00000000 03:06 786534     /lib/ld-2.5.so
b7fa2000-b7fa4000 rw-p 00019000 03:06 786534     /lib/ld-2.5.so
bfbf0000-bfc05000 rw-p bfbf0000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Initializing nautilus-open-terminal extension
Initializing gnome-mount extension

(evolution-2.10:6147): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-cups-icon:6163): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6149): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
-----------------------------------------------------------------------------------------------------

Checked the .ICEauthority file, belongs to me and has permissions 0600.
Any hints how to fix this?

best regards
Ray

---

### Post by kerry_s on 2007-05-02
It looks like a memory problem to me, use the live cd and check the memory.

---

### Post by ray007 on 2007-05-03
> **kerry_s said:**
> It looks like a memory problem to me, use the live cd and check the memory.

I don't think it's a memory problem since I can create a new user on the system and log into a gnome session without any problems. something (I suspect nautilus) corrupts its own memory and then crashes everything

---

### Post by ray007 on 2007-05-03
I have tracked the problem down the the **where**, but I still don't know **why**. After selectively removing parts of the configuration it ended up with the fault being in ~/.gconf/apps/gnome-session.
After removing this directory everything worked fine again.
the file ~/.gconf/apps/gnome-session/options/%gconf.xml contained this:
-----------------------------------------------------
<?xml version="1.0"?>
<gconf>
        <entry name="show_splash_screen" mtime="1177932124" type="bool" value="true">
        </entry>
        <entry name="auto_save_session" mtime="1158684081" type="bool" value="true">
        </entry>
        <entry name="splash_image" mtime="1177932124" type="string">
                <stringvalue>/home/ray/.gnome2/gnome-art/download/splashscreens/Splash-Black-Art3.png</stringvalue>
        </entry>
</gconf>
---------------------------------------------------
nothing more, nothing less ... anybody an idea what went wrong here?

best regards
Ray

---

### Post by jaywee on 2007-05-08
that helps me, too. the problem really gives me a big headache, and thanks to your tip!

---

### Post by BOBSONATOR on 2007-05-13
> **kerry_s said:**
> You forgot the & after fbsetbg -l, it should be

fbsetbg -l &

but you should put that in the init file.
look for
session.screen0.rootCommand:
and change to
session.screen0.rootCommand:	fbsetbg -l


I did all of this, and still am having the same problem, the wallpaper shows up, but the error is still there,

i appreciate the help.

---

### Post by RedSquirrel on 2007-05-13
> **BOBSONATOR said:**
> I did all of this, and still am having the same problem, the wallpaper shows up, but the error is still there,

i appreciate the help.


Try putting this line at the bottom of ~/.fluxbox/startup:

```
exec /usr/bin/fluxbox
```Make it the last line in that file.


EDIT:

If you want logging, use this line instead:

```
exec /usr/bin/fluxbox -log "~/.fluxbox/log" 
```

---

