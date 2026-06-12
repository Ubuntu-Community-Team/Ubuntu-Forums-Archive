---
title: "Is there some manual or an e-book for terminal commands"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-05-05
you know, I can't just post in the forums everytime I need to know 1 command.
I like manuals. they are just like the bible ... like I can't live as a web programmer without php manual or smarty manual ... I mean something that I can download as an e-book or html files. 

Thanks.

---

### Post by patrick295767 on 2006-05-05
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Proce

---

### Post by audaz on 2006-05-05
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by r4ik on 2006-05-05
[QUOTE=patrick295767][http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Proce[/QUOTE]

Nice one thanks.

---

### Post by cgjones on 2006-05-05
Use the man pages. It doesn't get much handier.

---

### Post by confused57 on 2006-05-05
[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)

[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)

[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

[http://www.techenclave.com/forums/linux-shortcuts-and-commands-65415.html](http://www.techenclave.com/forums/linux-shortcuts-and-commands-65415.html)

[http://www.tuxfiles.org/linuxhelp/sysadmin.html](http://www.tuxfiles.org/linuxhelp/sysadmin.html)

[http://www.faqs.org/docs/lnag/lnag_commands.html](http://www.faqs.org/docs/lnag/lnag_commands.html)

[http://linux.about.com/od/commands/l/blcmds.htm](http://linux.about.com/od/commands/l/blcmds.htm)

---

### Post by elamericano on 2006-05-05
[QUOTE=cgjones]Use the man pages. It doesn't get much handier.[/QUOTE]
Very true. Unfortunately, many times you don't know the command exists or that it's capable of doing what it does. Browsing through /bin /sbin /usr/bin and /usr/sbin is as informative as it gets, but extremely time consuming. Obviously a guide provides more direction, helping you learn what you should learn first.

---

### Post by nanotube on 2006-05-05
[QUOTE=elamericano]Very true. Unfortunately, many times you don't know the command exists or that it's capable of doing what it does. Browsing through /bin /sbin /usr/bin and /usr/sbin is as informative as it gets, but extremely time consuming. Obviously a guide provides more direction, helping you learn what you should learn first.[/QUOTE]
there is always "man -k" :)

also, you could try going to the first link in my sig, section "other commandline resources", and there are a bunch of tutorials and ebooks listed you could check out.

---

### Post by barbarian on 2006-05-05
some zsh tips:

[http://successtheory.com/tips/zshtips.html](http://successtheory.com/tips/zshtips.html)

:cool:

---

### Post by cgjones on 2006-05-05
[QUOTE=elamericano]Very true. Unfortunately, many times you don't know the command exists or that it's capable of doing what it does. Browsing through /bin /sbin /usr/bin and /usr/sbin is as informative as it gets, but extremely time consuming. Obviously a guide provides more direction, helping you learn what you should learn first.[/QUOTE]

That's why there is man -k, or apropos, or whatis. It's all right there, and it's all searchable.

---

### Post by aysiu on 2006-05-05
This is a one-page PDF document:
[http://homepage.powerup.com.au/~squadron/linux_manual.pdf](http://homepage.powerup.com.au/~squadron/linux_manual.pdf)

---

### Post by Isoss on 2006-05-05
Thanks guys ... you've been helpful .. but I am still looking for something downloadable. I prefere HTML folder which I can add it to my localhost folders. I googled but no luck ...

Thanks

---

### Post by aysiu on 2006-05-05
[QUOTE=Isoss]Thanks guys ... you've been helpful .. but I am still looking for something downloadable.[/QUOTE] The PDF I linked to isn't downloadable...?

---

### Post by cgjones on 2006-05-05
This is a great site for all sorts of information
[The Linux Documentation Project](http://www.tldp.org/)

This should be kind of what you are specifically looking for
[GNU/Linux Command-Line Tools Summary](http://www.tldp.org/LDP/GNU-Linux-Tools-Summary/html/index.html)

---

### Post by barbarian on 2006-05-05
> This is a one-page PDF document:
[http://homepage.powerup.com.au/~squa...nux_manual.pdf](http://homepage.powerup.com.au/~squa...nux_manual.pdf)

Thanks Aysiu, I've just downloaded it.

---

### Post by Isoss on 2006-05-05
[QUOTE=aysiu]The PDF I linked to isn't downloadable...?[/QUOTE]
Sorry, I writing this post while you posted that link .. thanks. I'll download it.

Thanks a bunch :D

---

### Post by mybootorg on 2006-05-05
[QUOTE=patrick295767][http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Proce[/QUOTE]

Wow, I looked for something like this for a week and couldn't find it.  Most of the command manuals out there approach things from a "I need to do this, how do I do it?" standpoint.

Whereas the link above teaches you from the ground up, walking around a linux system changing directories, to basic commands, to taking those basic commands and piping the the input/output to another command.  Which of course, is where the true power is at.

Now if I could just find a pocket reference of the same without having to print it out and fold it up in my pocket where it's going to going through the laundry.  Most of the Linux books I've found are aimed at the particular distro, and worse, aren't structured as nicely as the link above.

---

### Post by mybootorg on 2006-05-05
(accidental repost.  Please ignore)

---

### Post by elamericano on 2006-05-06
Oh great, I was beezing through one of those tutorials (I have a decent amount of experience), trying anything I didn't recognize, when I got to:

startx -- :1

Well, it didn't work, even as root, but I wasn't that surprised. Trouble is, now my OSD doesn't work. Oh well. That is the other way to learn linux. Experiment and break stuff, then try to fix it. That's how I became an expert in boot loaders. Let's hope the trend continues :)

---

### Post by skippy81 on 2006-05-06
The pdf file is pretty cool :p 

A really good way of finding a command out is using > man -k keyword where keyword is what you want to do.  For instance if I want to see a list of module related commands a "man -k module" shows me most of the appropriate command options at my disposal.

---

### Post by professor_chaos on 2006-05-06
for debian based common commands this is my bible.
[http://people.debian.org/~debacle/refcard/refcard-en-a4.pdf](http://people.debian.org/~debacle/refcard/refcard-en-a4.pdf)

---

### Post by Isoss on 2006-05-06
[QUOTE=professor_chaos]for debian based common commands this is my bible.
[http://people.debian.org/~debacle/refcard/refcard-en-a4.pdf](http://people.debian.org/~debacle/refcard/refcard-en-a4.pdf)[/QUOTE]


Thanks man, that is a good one .. still need something more like I can't call that a bible, that's more like a prayer book! ...

[http://www.linuxcommand.org/](http://www.linuxcommand.org/) is soooooooooooooo cool ... so you see the way they demonstrate everythin about linux commands? that's what I'm looking for but as something downloadable and can be explored offline.

---

### Post by Omnios on 2006-05-06
This is my Know yur terminal commands thread. WIth reference, basics and advanced page links.

 [http://ubuntuforums.org/showthread.php?t=45651]("http://ubuntuforums.org/showthread.php?t=45651")

---

