---
title: "synaptic, apt-get, and aptitude"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by yosef on 2006-10-27
If I download sometthing with synaptic and it ruins stuff, is it better for me to apt-get remove it or aptitude remove it?

---

### Post by Ben Sprinkle on 2006-10-27
It does the same thing.

---

### Post by Archmage on 2006-10-27
Aptitude should always be preferd. It is Apt-get with additional features (like removing unused things).

---

### Post by zvacet on 2006-10-27
I don´t know how synaptic can ruin something,but if it´s your case you can remove app with synaptic.If you want to remove it for good go to the /var/cahe/apt/archives.Find package you want to remove,become root and type in console rm -r filename.

---

### Post by mawaru on 2006-10-27
Is it true that if you use apt-get to install you have to use apt-get to uninstall?  The same goes for aptitude.  I thought I read that somewhere...

---

### Post by yosef on 2006-10-27
Well, I guess it wasn't actually synaaptic that ruined it, it was what I downloaded, xgl or compriz I think (although I downloaded at the same time tomboy, kmymoney, brightside, yakuake, and k9copy.) but now when I logon I just get the logon screen over and over again even if I try a failsafe session.  I can only do a console logon.  My wifi won't work now in the console logon either, so I have no internet connection on that laptop.  I am so frustrated.  Thank you guys for the info I will try getting rid of those packages, if you have any other suggestion please please post them

---

### Post by bulldog on 2006-10-27
> **mawaru said:**
> Is it true that if you use apt-get to install you have to use apt-get to uninstall?  The same goes for aptitude.  I thought I read that somewhere...

Synaptic and apt-get are the same.
You can install and uninstall programs.

But if the program needs additional dependency's they will be installed with the program,but when you decide to remove the program,the dependency's stay unused on your hard-drive,so far synaptic and apt-get.

When you use aptitude to install and uninstall it will remove all the dependency's which came with any program.
But you have to use it to install and uninstall.

You can use aptitude to install and apt-get to uninstall however,but the dependency story is not going to work then.

---

### Post by yosef on 2006-10-27
so what if its one of the dependencies that came with compriz or whatever and thats what screwed up my system?  How can I find out what it is and get rid of it or fix it?

---

### Post by bulldog on 2006-10-27
> **yosef said:**
> so what if its one of the dependencies that came with compriz or whatever and thats what screwed up my system?  How can I find out what it is and get rid of it or fix it?


Well you installed it so you should now.

I wasn't there at all so I'm not guilty.:D

---

### Post by mawaru on 2006-10-27
The problem I'm having is with a manual installation.  I downloaded several .deb files to resolve a problem I am having playing .avi files.  (There are too many dependencies so I gave up ](*,) ).  I'm now trying to remove the packages installed one by one.  I tried to use adept (I'm running kubuntu 6.06) to uninstall each package that was listed as "BREAK" (I think?).  That didn't work.  So I guess I should just use "apt-get remove" right?  

Thanks!

---

### Post by yosef on 2006-10-27
well, in synaptic all I did was check the box next to what I wanted, the dependencies came along for the ride.  I guess I probably should have paid more attention and taken note of what those dependencies were, but I didn't... do you have any advice for this situation?

---

### Post by Ben Sprinkle on 2006-10-27
> **synectics said:**
> It does the same thing.

> **bulldog said:**
> Synaptic and apt-get are the same.
You can install and uninstall programs.

But if the program needs additional dependency's they will be installed with the program,but when you decide to remove the program,the dependency's stay unused on your hard-drive,so far synaptic and apt-get.

When you use aptitude to install and uninstall it will remove all the dependency's which came with any program.
But you have to use it to install and uninstall.

You can use aptitude to install and apt-get to uninstall however,but the dependency story is not going to work then.
What we said, it makes no difference.

---

### Post by bulldog on 2006-10-27
> **mawaru said:**
> The problem I'm having is with a manual installation.  I downloaded several .deb files to resolve a problem I am having playing .avi files.  (There are too many dependencies so I gave up ](*,) ).  I'm now trying to remove the packages installed one by one.  I tried to use adept (I'm running kubuntu 6.06) to uninstall each package that was listed as "BREAK" (I think?).  That didn't work.  So I guess I should just use "apt-get remove" right?  

Thanks!

It's best to remove what is broken and can't been fixed by synaptic.

Did you have a look at Automatix?
It can install a whole lot of multmedia codecs,fonts,and a lot more.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Take a look and read some,I used it all the time when I do a fresh install and never had a problem with it.
You should choose automatix2 because automatix1 is going to be obsolete soon.

---

### Post by bulldog on 2006-10-27
> **yosef said:**
> well, in synaptic all I did was check the box next to what I wanted, the dependencies came along for the ride.  I guess I probably should have paid more attention and taken note of what those dependencies were, but I didn't... do you have any advice for this situation?

Do you use Edgy or Dapper?

And what did you install exactly?

Where there no dependency errors?

[QUOTE]What we said, it makes no difference.[QUOTE]

Yes it does as a matter of fact.

Apt get will not remove dependency's which where installed and synaptic doesn't either.

But as said aptitude does.
So use as much as you can aptitude to install and uninstall to keep your install clean.

You can take a look at this thread to see some programs and ways to get rid of your unused packages.

[http://ubuntuforums.org/showthread.php?t=140920%3Cbr%20/%3E](http://ubuntuforums.org/showthread.php?t=140920%3Cbr%20/%3E)

---

### Post by mawaru on 2006-10-27
> **bulldog said:**
> It's best to remove what is broken and can't been fixed by synaptic.

Did you have a look at Automatix?
It can install a whole lot of multmedia codecs,fonts,and a lot more.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Take a look and read some,I used it all the time when I do a fresh install and never had a problem with it.
You should choose automatix2 because automatix1 is going to be obsolete soon.
Thanks Bulldog.  I tried to install Automatix2, but had problems when I was trying to update.  I don't think the certificate was correctly added.  I'll try to figure that one out and uninstall the stuff that doesn't work.

---

### Post by yosef on 2006-10-27
I am running dapper kubuntu, I installed xgl and compriz, and then a few little programs: brightside, tomboy,kmymoney, yakuake, and k9copy.  Since I rebooted the login screen repeats endlessly unless I do a console login... I am really pretty lost here...

---

### Post by bulldog on 2006-10-27
> **yosef said:**
> I am running dapper kubuntu, I installed xgl and compriz, and then a few little programs: brightside, tomboy,kmymoney, yakuake, and k9copy.  Since I rebooted the login screen repeats endlessly unless I do a console login... I am really pretty lost here...

Is there no error message?

Type in console```
sudo dpkg-reconfigure -phigh  xserver-xorg
```
to try to reset things.

Why you use xgl/compiz and not beryl and emerald?

Which howto did you use?

---

### Post by yosef on 2006-10-27
I actually haven't used them yet... I only just last night downloaded them and then rebooted... and I guess you know the rest.  I read about them in an article wanted to try them out... you recomend using beryl and emerald instead.

---

### Post by yosef on 2006-10-27
And there isn't any error message, I just login the screeen goes blank as it loads then, lo and behold! its the logon screen again!  Very frustrating.

---

### Post by bulldog on 2006-10-27
Well I use Beryl and Emerald and it works fine.

I'm not familiar with all the packages you've installed but if you didn't make a change in any config file it can't be the course of the malfunction.

But if you uninstall everything you installed for compiz you can give Beryl a go.

Did the reconfigure anything?

You installed compiz and didn't configured it?
Just uninstall everything and reboot.

---

### Post by compmodder26 on 2006-10-27
A good way to tell what dependencies are used by a package in synaptic is to look at the package properties. Just click on the package name and then click properties in the toolbar.

---

### Post by thornomad on 2006-10-27
back to the aptitude/apt-get install/uninstall issue for a minute ... I have a follow up question:

using aptitude, I installed a program that allows me to connect to a SFTP server and mount the contents in an empty folder of my choice (i can't remember the name, am away from home).  anyway, this program depends on FUSE ... is one of the dependencies that was installed via aptitude.

now: I compiled another program that relies on FUSE and does a similiar number of webDav connections ...

my question is: if I later wanted to remove the first program via aptitude, would aptitude see the the second program depends on a dependency that was initially installed by the first and leave it alone ? or would both stop working ?

---

### Post by compmodder26 on 2006-10-27
> **thornomad said:**
> back to the aptitude/apt-get install/uninstall issue for a minute ... I have a follow up question:

using aptitude, I installed a program that allows me to connect to a SFTP server and mount the contents in an empty folder of my choice (i can't remember the name, am away from home).  anyway, this program depends on FUSE ... is one of the dependencies that was installed via aptitude.

now: I compiled another program that relies on FUSE and does a similiar number of webDav connections ...

my question is: if I later wanted to remove the first program via aptitude, would aptitude see the the second program depends on a dependency that was initially installed by the first and leave it alone ? or would both stop working ?

When you compiled the other program, did you use checkinstall?  If not then fuse will most likely get removed because aptitude doesn't know the other software exists.

---

### Post by thornomad on 2006-10-27
> **compmodder26 said:**
> When you compiled the other program, did you use checkinstall?  If not then fuse will most likely get removed because aptitude doesn't know the other software exists.

I did not use checkinstall ... if I had would that communicate  with aptitude ? 

need to read up on that ... heard of it but never used.

---

### Post by compmodder26 on 2006-10-27
> **thornomad said:**
> I did not use checkinstall ... if I had would that communicate  with aptitude ? 

need to read up on that ... heard of it but never used.

Yes, checkinstall would make apt aware of the programs existance. It would also let you uninstall the program through apt as well.

---

### Post by yosef on 2006-11-05
how much of a difference is it if I download the source and compile programs myself ascompared to aptituding them?

---

