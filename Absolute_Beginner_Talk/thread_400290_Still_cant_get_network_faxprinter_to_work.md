---
title: "Still cant get network fax/printer to work"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by mpooley on 2007-04-03
Hi
I have been trying to install a brother fax-1940cn color printer/fax onto my network ever since i dumped windows (two weeks!)

I have followed the instructions from the brother site to the letter but the ppd file never gets into the CUPS list of printers. today i tried to install using terminal and noticed that i am getting an error whilst installing.
I installed the driver packages first and got no errors and then installed the cups wrapper:
sudo  dpkg -i --force-all cupswrapperfax1940cn_1.0.0-1_i386.deb

this is the result. Notice that the ppd file does not get copied!
does anyone know what is wrong?

(Reading database ... 168462 files and directories currently installed.)
Preparing to replace cupswrapperfax1940cn 1.0.0-1 (using cupswrapperfax1940cn_1.0.0-1_i386.deb) ...
lpadmin: The printer or class was not found.
/etc/init.d/cups: Command not found.
Unpacking replacement cupswrapperfax1940cn ...
Setting up cupswrapperfax1940cn (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperFAX1940CN
/etc/init.d/cups: Command not found.
lpadmin: Unable to copy PPD file!

---

### Post by josephus on 2007-04-04
I stumbled upon this post after seeing your other post of trying to modify debian files which I assume is related to this post.

Anyway, I am curious as to why you used the force-install option?  Generally, you should  not use that option unless absolutely necessary as things tend to break.

To install the printer properly you first need to install the lpr file
[http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/fax1940cnlpr-1.0.2-1.i386.deb](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/fax1940cnlpr-1.0.2-1.i386.deb)

I found that when I tried to install this that there was error, that I resolved by first adding a directory:
```
sudo mkdir /var/spool/lpd
sudo dpkg -i fax1940cnlpr-1.0.2-1.i386.deb

```
After that I installed cupswrapperfax1940cn_1.0.0-1_i386.deb .  Like you, I ran into a couple of errors.  You need to link cups to cupsys
```

cd /etc/init.d
sudo ln -s cupsys cups

```
then install 
```
sudo dpkg -i cupswrapperfax1940cn_1.0.0-1_i386.deb
```

You still get the error message about the ppd file, but according to this you can ignore it:
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#60](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#60)

Hope this helps.

edit: you should probably remove the symbolic link (/etc/init.d/cups) after installation

---

### Post by mpooley on 2007-04-04
Thanks!
Unfortunately i found an old thread which told me how to change the package before i saw your reply!

Your way looks easier! :)

Basicly I'm struggling to understand half of what i'm reading and just copying code like yours which is very helpfull but is over my head most of the time.
Still i think its the only way i will learn - i just hope i'll remember it all in a few months ;)

---

### Post by josephus on 2007-04-04
well, that package would be tricky to install fir anyone who is just getting used to linux.  brother did a really bad job packaging it, this why linux gets a reputation of not being user friendly.

whenever you are trying new commands its good to have some idea what they are doing before blindly copy and pasting.  use the man pages (i.e. man <cmd>) or look at the help file: <cmd> --help .  It's not necessary to read through the whole thing,  just the first couple of lines to know what the command is all about.  anyway good luck in getting everything up and running.

---

### Post by mpooley on 2007-04-04
Thanks!

After a couple more hours I have got it to work!!

There were several small probs but the final one was that i needed java runtime installed which i hadn't !!
It would have been nice if the program had come up with an error to tell me rather than just bombing!

I have one or two more niggly things to get right so i shall start  another thread.

---

