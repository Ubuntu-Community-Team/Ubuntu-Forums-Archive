---
title: "no sudo gedit??"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by F Cocquyt on 2006-05-27
Hi group,

I am having some trouble with my text editor gedit. When I try to edit a file, I can start gedit using the console if I only log in as non-root. When I try to edit the file as root using the command sudo gedit my text editor doesn't start. :???:   

Anybody got an idea what might be wrong?

Ubuntu version: Dapper.

regards,
Frederik.

---

### Post by ed_agamemnon on 2006-05-27
i have exactly the same problem myself.

i've posted something about it somewhere on the forum but have yet to find a solution...

must be a bug. can't think what's caused it though, so i can't file anything worthwhile.

---

### Post by dmizer on 2006-05-27
sudo with gedit hasn't worked for me for quite some time.  i just use nano in the command line instead.  and it:s not as difficult to get the hang of as some of the other options out there (at least in my opinion)

---

### Post by aysiu on 2006-05-27
Have you tried this? ```
gksudo gedit
```

---

### Post by F Cocquyt on 2006-05-27
I've just tried is. Doesn't seem to work either. I get 

(gedit:5094): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by aysiu on 2006-05-27
[QUOTE=F Cocquyt]I've just tried is. Doesn't seem to work either. I get 

(gedit:5094): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/QUOTE] Sure it does. I get that "error," too, but it works...

Or is this what you see? ```
fcocquyt@ubuntu:~$gksudo gedit
(gedit:5094): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
fcocquyt@ubuntu:~$
``` and no gedit window?

---

### Post by F Cocquyt on 2006-05-27
>  and no gedit window?

If I want to edit a specific document I don't get a gedit window. 
[ATTACH]10153[/ATTACH]

If I want to start a new document, It's like the editor doesn't load completely. 
e.g. There are no menu's present
[ATTACH]10154[/ATTACH]

---

### Post by richbarna on 2006-05-27
ok so use vi or vim
sudo vim ....................
Goto what you need to edit and click the insert button, and edit.
You normally click "tab" twice in succession to exit.
You can then type : wq (which = write and quit).
I always use vi, no probs with gedit, kate or the other gui editors.

---

### Post by F Cocquyt on 2006-05-27
[QUOTE=richbarna]ok so use vi or vim

[/QUOTE]
I've already worked with vi and didn't like it that much that's why I changed to gedit. 

I could go back, but the fact still remains that gedit doesn't work and I would like to know why, It might be something bigger than just gedit ....

---

### Post by aysiu on 2006-05-27
[QUOTE=F Cocquyt]I've already worked with vi and didn't like it that much that's why I changed to gedit. 

I could go back, but the fact still remains that gedit doesn't work and I would like to know why, It might be something bigger than just gedit ....[/QUOTE] If you didn't get the screenshot I posted earlier, then, yes, there's something bigger wrong with your Ubuntu than just Gedit.

---

### Post by F Cocquyt on 2006-05-28
[QUOTE=aysiu]If you didn't get the screenshot I posted earlier, then, yes, there's something bigger wrong with your Ubuntu than just Gedit.[/QUOTE]

That's what I was thinking aswell. Are there any tips anybody could give me to do a big checkup to see what might be wrong?

---

### Post by TheTux on 2006-05-28
how about su?
have u tried....su and then gedit

---

### Post by richbarna on 2006-05-28
[QUOTE=TheTux]how about su?
have u tried....su and then gedit[/QUOTE]
If you su + passwd, it's the same as using sudo or gksudo before the command.
su = switch-user, which gives you root priveledges either way.

---

### Post by F Cocquyt on 2006-05-28
sudo + su shows some configuration errors(see below). Could this be the cause of some of my trouble?

configuratiefout - onbekend item 'QUOTAS_ENAB' (waarschuw een systeembeheerder)
configuratiefout - onbekend item 'NOLOGIN_STR' (waarschuw een systeembeheerder)
configuratiefout - onbekend item 'ENV_HZ' (waarschuw een systeembeheerder)
configuratiefout - onbekend item 'CHFN_AUTH' (waarschuw een systeembeheerder)
configuratiefout - onbekend item 'CLOSE_SESSIONS' (waarschuw een systeembeheerde r)

---

### Post by richbarna on 2006-05-28
What does this mean in English? :-
> (waarschuw een systeembeheerder)
Is it something to do with "system headers"?
Why not go into synaptic, type "headers" and see if you have the kernel headers installed.
Also, your screenshot in message #7 shows apache.
Under headers in the repository,(I looked in Adept, you've got Synaptic) there are some related to apache as well.
Maybe this might help?

EDIT: Just found out from another Belgian post that it means :-
(warn a systemadmin) (waarschuw een systeembeheerder)
The other user has psoted a problem trying to use "sudo" as well.
I think this maybe a root password problem
see this :-
[http://www.ubuntuforums.org/showthread.php?t=183589]("http://www.ubuntuforums.org/showthread.php?t=183589")

---

### Post by F Cocquyt on 2006-05-28
Thanks for the link, but as far as I can see he hasn't found the solution either. 

As what the headers is concerned: I've installed the headers and the linux-headers-server and restarted my laptop, but still no succes. I'll keep on looking for a possible solution.

---

### Post by richbarna on 2006-05-28
I found this :-
[Ubuntu Login Definitions]("https://wiki.ubuntu.com/LoginDefs")
There is a part for QUOTAS_ENAB
> # Enable setting of ulimit, umask, and niceness from passwd gecos field.
#
QUOTAS_ENAB             yes


and for NOLOGIN_STR 
> # If defined, the presence of this value in an /etc/passwd "shell" field will
# disable logins for that user, although "su" will still be allowed.
#

NOLOGIN_STR     NOLOGIN


Maybe there is a problem with your "/etc/login.defs" file.

---

### Post by dmizer on 2006-05-29
i wonder how many people with this problem are using the anthy uim for international input?

there is a bug that affects gedit and the gnome print manager noted here: [https://launchpad.net/distros/ubuntu/+source/uim/+bug/27355](https://launchpad.net/distros/ubuntu/+source/uim/+bug/27355)

> Yes, all uim Packages in Breezy are compiled with
--enable-debug. Just get the source package extract it and have a look in debian/rules. There you will see the --enable-debug flag is set. Just deleting this line and recompile will not only solve the problem with gnome-cups-manager but also some issues when gedit is crashing if opening a shell script. All chrashes related to an active uim will not occour when recompiled without --enable-debug flag!

---

### Post by ed_agamemnon on 2006-05-29
not me... standard input.

hmm...

---

### Post by F Cocquyt on 2006-05-29
[QUOTE=dmizer]i wonder how many people with this problem are using the anthy uim for international input?
[/QUOTE]

just a short question: what is the anthy uim for international input? :confused:  and how can I check if I'm using it or not? (If it's something I had to install manually I don't think it's installed.)

---

### Post by dmizer on 2006-05-29
[QUOTE=F Cocquyt](If it's something I had to install manually I don't think it's installed.)[/QUOTE]
it would have to have been something you installed yourself.  it's not part of the standard ubuntu released packages.

if you want to check, just open synaptic and do a search for anthy or uim, and see if it's loaded or not.

---

### Post by F Cocquyt on 2006-05-30
Nope, it's not loaded. I've searched both uim and anthy. Does anybody have another idea?

---

### Post by F Cocquyt on 2006-06-03
apperently my local loopback didn't load at bootup. I've booted it up and it works. 
can anyone tell me how to let this start at boot?

---

### Post by Mustard on 2006-06-03
[QUOTE=F Cocquyt]apperently my local loopback didn't load at bootup. I've booted it up and it works. 
can anyone tell me how to let this start at boot?[/QUOTE]

So sudo gedit is working now?  That's interesting.

I'm not sure about setting up local loopback.  I've seen this issue pop up before though, local loopback not starting up, so the answer exists somewhere on the forum if  you want to  use the search function.

---

