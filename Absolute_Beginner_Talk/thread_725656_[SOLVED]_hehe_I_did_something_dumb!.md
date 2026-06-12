---
title: "[SOLVED] hehe I did something dumb!"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by leadhead on 2008-03-15
Let see if I can get this across clearly enough as I am a linux novice.

I was trying to get my laptop to play a DVD. Totem, VLC and I think Xine...None of them seem to want to play my dvd. Then I saw a thread about installing Gstreamer plugins and so I marked them for install. I got some error saying Ubuntu couldnt do it.

So being the maverick that I am, I downloaded the plugins to my desktop and tried to install them. I thought perhaps I could run dpkg on the tarball...so when it didnt show up in the list of apps to run on the tarball, I typed dpkg in the custom command line...thinking it would "search for it" well, nothing happened and I didnt think much of it and tried to sudo install-sh inside the extracted directory on the desktop...a bunch of scrolling text to the effect of "WRONG" "FAIL" WHATS WRONG WITH YOU" pass through the terminal screen LOL!

This act apparently made ubuntu mad because when I tried to open the synaptics package manager, I got E: dpkg was interuppted run dpkg --configure -a to fix the problem...

Now I thought that when I had typed in the custom application, that I inadvertantly created some file that was hanging up the works LOL! So I went into /usr/bin and deleted dpkg. I saw the dpkg-deb and thought that was the real package manager file and that plain dpkg was the file I inadvertantly created. Wrong again!

I cannot now run dpkg --configue -a because..."this command doesnt exist":lolflag:

If I have to reinstall, that is fine. I installed ubuntu on my laptop to learn about linux for my job. While you guys may think I should never touch a computer again, I do it on purpose to learn. I have already learned a ton about how this operating system works. I like this OS, it is a blast to mess around with.

Anyways, is it possible to dig myself out of this hole? Without reinstalling? Or is it just best to just wipe it and start over?

---

### Post by Diabolis on 2008-03-15
lol If I were you I would wreck the system further more just to see what you can find out and then make a clean install.

---

### Post by PmDematagoda on 2008-03-15
When you said you attempted to fix the issue with a dpkg command, was it:-
```
sudo dpkg --configure -a
```
or
```
sudo dpkg --configue -a
```
?

The latter command is incorrect, you need the first command.

---

### Post by patrickaupperle on 2008-03-15
WOW. I don't know that much about the innerworking of linux, but it sounds like you messed up your installation pretty bad. I am pretty sure someone will come up with something to fix it, though I don't know what. Don't be disapointed if no one does, though. I thought I messed up my vm pretty bad, but what I did was nothing in comparison to that. :lol: :lol:

:lolflag:

---

### Post by leadhead on 2008-03-15
It was definately the former. I reran the command to make sure I didnt fat finger it.

---

### Post by steveneddy on 2008-03-15
[This]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Menu_Method_for_Adding_Repositories") is where you needed to look for instructions on how to do things in Ubuntu.

After you reconfigure, go to this web site and get some repositories added and then update again.

You can cut/paste from the page to your terminal.

Please look over[ the entire site]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy"), as it will help you more than any other site.

---

### Post by PmDematagoda on 2008-03-15
> It was definately the former. I reran the command to make sure I didnt fat finger it.

Are you sure that everything was right? Keep in mind that Linux is very specific with commands, if you make one small typo then it becomes a whole different command for Linux.

---

### Post by leadhead on 2008-03-15
Oh yeah, 

I am a Windows IT Admin!:lolflag:

---

### Post by leadhead on 2008-03-15
> **PmDematagoda said:**
> Are you sure that everything was right? Keep in mind that Linux is very specific with commands, if you make one small typo then it becomes a whole different command for Linux.


I copied and pasted your command into my terminal and still no joy.

---

### Post by PmDematagoda on 2008-03-15
> **leadhead said:**
> Oh yeah, 

I am a Windows IT Admin!:lolflag:

I am not underestimating your knowledge in anyway when I say this so please don't feel offended if I say this, but could you please copy and paste the command I mentioned into a terminal and try to execute it?

---

### Post by PmDematagoda on 2008-03-15
> **leadhead said:**
> I copied and pasted your command into my terminal and still no joy.

That is very strange.

Can you post the result of:-
```
dpkg --version
```

---

### Post by leadhead on 2008-03-15
> **steveneddy said:**
> [This]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Menu_Method_for_Adding_Repositories") is where you needed to look for instructions on how to do things in Ubuntu.

After you reconfigure, go to this web site and get some repositories added and then update again.

You can cut/paste from the page to your terminal.

Please look over[ the entire site]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy"), as it will help you more than any other site.

Bookmarked! and thank you as that is superbly helpfull!!

---

### Post by leadhead on 2008-03-15
> **PmDematagoda said:**
> That is very strange.

Can you post the result of:-
```
dpkg --version
```

> leadhead@leadhead-laptop:~$ dpkg --version
The program 'dpkg' is currently not installed.  You can install it by typing:
sudo apt-get install dpkg
bash: dpkg: command not found
leadhead@leadhead-laptop:~$ sudo apt-get install dpkg
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
:lolflag:

---

### Post by Diabolis on 2008-03-15
```
Now I thought that when I had typed in the custom application, 
that I inadvertantly created some file that was hanging up the works LOL!
So I went into /usr/bin and deleted dpkg. 
I saw the dpkg-deb and thought that was the real package manager file and that plain dpkg was the file I inadvertantly created. 
Wrong again!

```

He deleted dpkg, thats why the commands are not working.

As far as I know dpkg is the app that installs every other app, and since you deleted it you need to run dpkg to install dpkg lol, or am I wrong guys?

---

### Post by Sef on 2008-03-15
> Anyways, is it possible to dig myself out of this hole? Without reinstalling? Or is it just best to just wipe it and start over?

Depends on how much time you want me to figure out what you can do, if anything, about the problem.

> I am a Windows IT Admin!

And soon with enough time and patience, you will be able to be a GNU/Linux Administrator too.

---

### Post by leadhead on 2008-03-15
> **Diabolis said:**
> ```
Now I thought that when I had typed in the custom application, 
that I inadvertantly created some file that was hanging up the works LOL!
So I went into /usr/bin and deleted dpkg. 
I saw the dpkg-deb and thought that was the real package manager file and that plain dpkg was the file I inadvertantly created. 
Wrong again!

```

He deleted dpkg, thats why the commands are not working.

As far as I know dpkg is the app that installs every other app, and since you deleted you need dpkg to install dpkg or am I wrong?


You got it!

---

### Post by Diabolis on 2008-03-15
apt-get is an application that actually just facilitates the installation of applications, but in the inside it uses dpkg commands. So probably you'll have to download dpkg from a site.

---

### Post by Sef on 2008-03-15
Good catch Diabolis on this:

> He deleted dpkg, thats why the commands are not working.

If it is possible, you could try reinstalling dpkg from the command line:

```
sudo apt-get update
```

then

```
sudo apt-get install dpkg
```

That should reinstall the dpkg package.

If that doesn't work, then reinstalling would be your best option.

---

### Post by leadhead on 2008-03-15
> **Sef said:**
> Depends on how much time you want me to figure out what you can do, if anything, about the problem.



And soon with enough time and patience, you will be able to be a GNU/Linux Administrator too.


Dematagoda in post 13 instructed me to do that. It appears the package manager gets interrupted and needs the installer part of dpkg to make everything better...but I deleted that. 

I will just reinstall. I appreciate the instant support. I got the bookmark on how the package manager works so I will read that to understand in more detail what I did wrong. 

Thank you very much for your time!:KS

---

### Post by leadhead on 2008-03-15
> **Diabolis said:**
> apt-get is an application that actually just facilitates the installation of applications, but in the inside it uses dpkg commands. So probably you'll have to download dpkg from a site.


I will give that a shot. before I reinstall to see if I can make a go of it. If I am successfull, I will post what I did.

---

### Post by unutbu on 2008-03-15
leadhead, sorry to hear about your problem, and I hope you find a quick recovery.
That being said, thank you for your delightful posting style. I haven't laughed so hard in a long time.

---

### Post by PmDematagoda on 2008-03-15
> **leadhead said:**
> Dematagoda in post 13 instructed me to do that. It appears the package manager gets interrupted and needs the installer part of dpkg to make everything better...but I deleted that. 

I will just reinstall. I appreciate the instant support. I got the bookmark on how the package manager works so I will read that to understand in more detail what I did wrong. 

Thank you very much for your time!:KS

Did you try installing dpkg again? There could be a chance that your system can be rescued.

---

### Post by leadhead on 2008-03-16
Fixed it!

I booted the install cd and it splays out a filesystem image into memory which inlays a dpkg executable in /usr/bin so I copied the dpkg file to my HD. This allowed me to reboot to normal filesystem and sudo 'dpkg --configure -a' and then fix my broken software index with  sudo apt-get install -f

The problem software in the update manager which was actually the cause of this whole mess is the Sun java6 jre...it hangs during installation because it tries to past a graphic in the terminal window for the license agreement. I cant do anything to "click" ok. or enter or space bar or anything else that will advance the installer. 

It tells me before the install that its gona take up 96mb of disk space and do I want to continue. I just said no which canceled the install...

So I am back up and running.

It will be interesting to see if I have dpkg problems in the future since the file I copied from the CD might be a different version. Perhaps I should uninstall/reinstall it with synaptic if that is possible?

---

### Post by leadhead on 2008-03-16
Oh yeah, 


Thanks again for the prompt support!:guitar:

---

### Post by Diabolis on 2008-03-16
Cool, I'm glad you got it working again.

---

### Post by VraiChevalier on 2008-03-16
Now this has been quite educational (and entertaining)! 
Thanks to everybody for all the useful information.
<knocks wood> hoping to never need this useful information:lolflag:

---

### Post by Sef on 2008-03-16
Glad you got it working again.

---

### Post by PmDematagoda on 2008-03-16
> **Sef said:**
> Glad you got it working again.

Same here. Good work:).

---

### Post by leadhead on 2008-03-16
> **unutbu said:**
> leadhead, sorry to hear about your problem, and I hope you find a quick recovery.
That being said, thank you for your delightful posting style. I haven't laughed so hard in a long time.

:) Thanks for the compliment and glad I could provide the laughs.

I shouldnt say I am a total noob as I have some experience here or there. I know enough about Linux/Unix to accidentally level Moscow! Which in many instances makes me worse than someone that is just cracking open a cup of ubuntu. To make things worse, I am a shoot first and ask questions later type of IT guy. This makes me Fantastic with windows because I know it very well, not so fantastic with our phone server (Red Hat Enterprise 4...not nearly as cool as Ubuntu I am finding out). It came with nothing in terms of applications I...I want to install an Open rsm agent on it. In order to do that, I needed to install gcc compiler to compile the app. Guess what I found out? When trying to install my GCC compiler, I discovered that I NEEDED TO COMPILE IT!!! What kinda hole in the bucket h-e-double hockey sticks operating system is this?!! At this point, I realized that I needed to make a choice between serious education in Linux or continue to lose my hair. 

I realize that Ubuntu is way different than fedora or redhat, but the basics are the same, and I really need to figure out how to get around first anyways so... I actually was going to start with Gentoo and that was 4 hours of manually configuring my kernel (Yikes, what happens if you realize you forgot to add something like PPP support for eth0 after you compile your Kernel?) I did get it working...sort of, it booted with a bunch of errors...Ubuntu=easier to install than windows so here I am.

---

### Post by joshrobinson on 2008-03-16
ubuntu makes things real easy, when linux started it was constantly compiling code, then packages were introduced, but you would find a package you wanted to install, then it would say you need a dependency, then that dependency would have a dependency, and on and on

having a nice package manager that takes care of all of your dependencies makes things 1000x easier

---

### Post by leadhead on 2008-03-16
> **VraiChevalier said:**
> Now this has been quite educational (and entertaining)! 
Thanks to everybody for all the useful information.
<knocks wood> hoping to never need this useful information:lolflag:

A good thing to take away from my leg amputation for an ingrown toenail is that the installation cd will lay out the entire file structure of ubuntu for you to perhaps replace a file that is corrupted or missing for some reason.

 It would be a last resort of course as I posted earlier with the constant updates, the versions would probably be wrong. But it may allow your broken problem to work just enough for one of the knowledgable staffers to fix it or the software update thing to recognize you have an old version and download the update etc...

---

### Post by unutbu on 2008-03-16
Glad to hear you're back to... normal. :)
To follow up on your previous post:
> Perhaps I should uninstall/reinstall it with synaptic if that is possible?

```

sudo apt-get install dpkg --reinstall

```

---

