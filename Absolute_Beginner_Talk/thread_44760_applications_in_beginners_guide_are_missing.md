---
title: "applications in beginners guide are missing?"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-06-27
Ok...I may be asking a lot of questions for the next few days. Hope that's ok.

I have edited my sources file and I can now install remote add ons. Problem 1 is this:

In the guide it says to terminal to: sudo apt-get install flashplayer-mozilla to install flash player. I ran that command and get these results:

[B]ralph@RALPH:~ $ sudo apt-get install flashplayer-mozilla
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package flashplayer-mozilla
[/B]

I understand that the package location or filename is obviously wrong but what do I do about it?

The biggest problem I really need an answer to is this though. How do I install stuff I have downloaded? Do I extract it to the apt directory and then install it with sudo apt-?whathere? install filename (how do I know what file is the install file?

---

### Post by gammyhand on 2005-06-27
[QUOTE=gammyhand]Ok...I may be asking a lot of questions for the next few days. Hope that's ok.

I have edited my sources file and I can now install remote add ons. Problem 1 is this:

In the guide it says to terminal to: sudo apt-get install flashplayer-mozilla to install flash player. I ran that command and get these results:

[B]ralph@RALPH:~ $ sudo apt-get install flashplayer-mozilla
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package flashplayer-mozilla
[/B]

I understand that the package location or filename is obviously wrong but what do I do about it?

The biggest problem I really need an answer to is this though. How do I install stuff I have downloaded? Do I extract it to the apt directory and then install it with sudo apt-?whathere? install filename (how do I know what file is the install file?[/QUOTE]
 Also - 70% of what I try to install (from the guide) says "no installation candidate". I don't know what to do about that.

---

### Post by Ken.Lank on 2005-06-27
I'm in the n00b bucket too, but lets see if I can help.  After you added the additional repositories did you run:
```

sudo apt-get update

```

This will update the application list from the new repositories that you just added.

---

### Post by aysiu on 2005-06-27
[QUOTE=gammyhand]
I have edited my sources file and I can now install remote add ons. Problem 1 is this:
[/quote]

Can you post your /etc/apt/sources.list so we can see what you've changed it to?

> 
I understand that the package location or filename is obviously wrong but what do I do about it?

The biggest problem I really need an answer to is this though. How do I install stuff I have downloaded? Do I extract it to the apt directory and then install it with sudo apt-?whathere? install filename (how do I know what file is the install file?

Apt-get is a lot simpler than you think it is. Provided you have the correct name, *sudo apt-get install applicationname* not only downloads the application, but it also unpacks it and installs it.

A couple of things to help you out here.

First of all, changing your sources.list file isn't enough. After you do that, you need to type *apt-get update*. In fact, you should probably type that before you install any application, whether you've changed your sources.list file or not. *apt-get update* checks to see what's in your sources and finds the latest versions of them.

The second suggestion, if you're not sure about the name of a package, you may be better off installing software via Synaptic Package Manager instead of the command-line. Synaptic is a graphical version of apt-get. Instead of typing *apt-get update*, you click "Reload." Instead of guessing the name of a file, you can search for any part of the file name or even a word that would show up in the description of the application. Once you've selected the applications to install, you hit "Apply," and they'll install.

---

### Post by gammyhand on 2005-06-27
[QUOTE=Ken.Lank]I'm in the n00b bucket too, but lets see if I can help.  After you added the additional repositories did you run:
```

sudo apt-get update

```

This will update the application list from the new repositories that you just added.[/QUOTE]
 Yep I did thanks :) But only because terminal told me to run it to correct problems.

---

### Post by SGC on 2005-06-27
Did you do an **sudo apt-get update** after editing the source file. If you did that and still you get the error messages then please post your **/etc/apt/sources.list** here

For the packages that you downloaded it, the installition methode differ from file type to another. So what type of files did you downloded?

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=gammyhand]Ok...I may be asking a lot of questions for the next few days. Hope that's ok.[/QUOTE]

Its fine. 

> 
The biggest problem I really need an answer to is this though. How do I install stuff I have downloaded? Do I extract it to the apt directory and then install it with sudo apt-?whathere? install filename (how do I know what file is the install file?

The best way to install things is in synaptic. Go to "system" then "administration" then pick "synaptic package manager."

---

### Post by gammyhand on 2005-06-27
[QUOTE=poofyhairguy]Its fine. 



The best way to install things is in synaptic. Go to "system" then "administration" then pick "synaptic package manager."[/QUOTE]
 Aah...and that literally contains EVERY known linux package?

---

### Post by gammyhand on 2005-06-27
[QUOTE=gammyhand]Aah...and that literally contains EVERY known linux package?[/QUOTE]
 I have pressed reload on synaptic and I can't find the two things I need. 1) flash player. 2) ATI proprietry drivers.

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=gammyhand]Aah...and that literally contains EVERY known linux package?[/QUOTE]

If you do this:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

You will have access to the biggest repository of packages in the Linux world (in my experiance of judging distros on this quality).

No...not every package is there...Only one I ever wanted wasn't there...

But its the best Linux can offer. No other distro (except for maybe Gentoo or the unstable debian) has a bigger set of easy to install packages. New ones come in from the backport repository.

Its great. My favorite thing about Ubuntu. I dislike installing packages from source code (the "universal" Linux install method).

---

### Post by khwang on 2005-06-27
hope you don't mind if I jump into the fray.  :) 

In the unofficial Ubuntu starter guide, it says:

"How to install Web Authoring System (Nvu)?

sudo apt-get install nvu
"

nvu does not appear in the synaptic package manager.  Why not?

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=gammyhand]I have pressed reload on synaptic and I can't find the two things I need. 1) flash player. 2) ATI proprietry drivers.[/QUOTE]


Are you using the 64 bit version? Its for experianced Linux users....and it lacks many packages.

[http://www.ubuntuforums.org/showpost.php?p=231354&postcount=6](http://www.ubuntuforums.org/showpost.php?p=231354&postcount=6)

---

### Post by gammyhand on 2005-06-27
[QUOTE=poofyhairguy]Are you using the 64 bit version? Its for experianced Linux users....and it lacks many packages.

[http://www.ubuntuforums.org/showpost.php?p=231354&postcount=6](http://www.ubuntuforums.org/showpost.php?p=231354&postcount=6)[/QUOTE]
 Thanks. I will give the nerdy way a go. Can you explain what else I will see? Will I be able to install flash etc?

I really need my ATI drivers as I have dual screen which I am not prepared to give up on. Thanks for the help :)

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=gammyhand]Thanks. I will give the nerdy way a go. Can you explain what else I will see? Will I be able to install flash etc?

I really need my ATI drivers as I have dual screen which I am not prepared to give up on. Thanks for the help :)[/QUOTE]


Basically the nerdy way is to run the 32 bit version INSIDE the 64 bit version. Ubuntu runs well in itself.

I don't know about flash.....but there are new ATI drivers that use the 64 bit version of linux now (since hoary's release I think).

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

Install these pacakges:

> sudo apt-get install build-essential linux-headers


Then do this:

[http://www.ubuntuforums.org/showpost.php?p=122362&postcount=6](http://www.ubuntuforums.org/showpost.php?p=122362&postcount=6)

Good luck.

---

### Post by gammyhand on 2005-06-27
[QUOTE=poofyhairguy]Basically the nerdy way is to run the 32 bit version INSIDE the 64 bit version. Ubuntu runs well in itself.

I don't know about flash.....but there are new ATI drivers that use the 64 bit version of linux now (since hoary's release I think).

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

Install these pacakges:




Then do this:

[http://www.ubuntuforums.org/showpost.php?p=122362&postcount=6](http://www.ubuntuforums.org/showpost.php?p=122362&postcount=6)

Good luck.[/QUOTE]
 It sounds like I would be best transferring to the 32-bit version for ease of use. Would you agree? What exactly are the benefits of the 64-bit version apart from larger memory handling?

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=gammyhand]It sounds like I would be best transferring to the 32-bit version for ease of use. Would you agree? What exactly are the benefits of the 64-bit version apart from larger memory handling?[/QUOTE]

It makes you seem cooler? Seriously the 64 bit version needs a little more time in the oven. I would use the 32 bit one if I was you. This stuff is fairly new.

---

### Post by gammyhand on 2005-06-28
[QUOTE=poofyhairguy]It makes you seem cooler? Seriously the 64 bit version needs a little more time in the oven. I would use the 32 bit one if I was you. This stuff is fairly new.[/QUOTE]
 Thanks. I will swap. Is it common place to need to re-install about 10 times when you first start using / learning linux :D

---

### Post by poofyhairguy on 2005-06-28
[QUOTE=gammyhand]Thanks. I will swap. Is it common place to need to re-install about 10 times when you first start using / learning linux :D[/QUOTE]

More than that for me.

---

### Post by gammyhand on 2005-06-28
[QUOTE=poofyhairguy]More than that for me.[/QUOTE]
 Good good.

I can't at the moment see why I would want to go back to windows. I am thinking re: my mp3 player not working. Should I backup it's contents onto DVD's on a windows system and re-format it under ubuntu? Or is there a way to get it to read it's file system? (I think it is FAT16).

---

