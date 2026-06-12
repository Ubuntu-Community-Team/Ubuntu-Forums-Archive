---
title: "X11vnc X login"
date: 2011-05-26
forum: Any Other OS
---

### Post by Zhivargo on 2011-05-26
I have been trying to days have x11vnc connect to my login screen. 
I can start x11vnc only if the computer is already logged in, but since i want to wol, ssh in and then start the server remotely i need the ...erm... Xauthority? 

when i type in 

```
ps wwaux | grep auth
```


i get 


```
root     18411  1.2  2.6  71860 54964 tty8     Ss+  16:05   0:16 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-1j6Crh/database -nolisten tcp
myname     18589  0.0  0.3  26336  6284 ?        Sl   16:05   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
root     23994  0.0  0.0   4156   864 pts/2    S+   16:26   0:00 grep --colour=auto auth
```

**-auth /var/run/gdm/auth-for-gdm-1j6Crh/database**
according to guides should be the place of 
MIT-MAGIC-COOKIE
which would give me the authority to logon as a user 

X11vnc is used a fair bit i wonder if someone out there has had the same problem? i have been looking at guide after guide hehe its sending me crazy i hope someone can understand me and help!

i use mint 11 RC

---

### Post by bodhi.zazen on 2011-05-26
It is far easier to use an alternate VNC server. I suggest FreeNx

You could also use vnc4server.

Better, use ssh -X and skip VNC altogether.

---

### Post by krunge on 2011-05-26
Given what you've indicated, running the following command as root (or sudo) should export that display :0 
```
x11vnc -display :0 -auth /var/run/gdm/auth-for-gdm-1j6Crh/database
```
Is that not working for you?  If not attach the x11vnc output for the failed case to this thread.

In more recent x11vnc you can try (still as root/sudo):
```
x11vnc -display :0 -auth guess
```
and that will have x11vnc try to guess the auth file using the same heuristics you used to find it.

But a better way is to use the display manager's start up file.  For the display manager gdm you would likely edit /etc/gdm/Init/Default and put the x11vnc command line (with -bg x11vnc option to put it in the background) near the bottom of that script (but before the "exit 0".) In this mode you DO NOT use '-display' or '-auth' options.  The are already set to the correct values in the environment for you, that is why this method is preferred.  More info here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]
(see the section named 'Continously')

---

