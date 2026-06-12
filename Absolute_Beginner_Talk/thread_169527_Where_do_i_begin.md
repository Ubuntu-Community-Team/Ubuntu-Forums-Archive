---
title: "Where do i begin?"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by ckonrad on 2006-05-02
I am completly lost i mean i feel like i just started learning how to use a computer and i have been using them my whole life. How do i do "anything" on ubuntu? It doesnt matter what i do i get an error message aside from browsing the internet but trying to program with python or java, downloading "anything" no matter what i download it just gives me an error message. I cant even download an mp3 that rythmbox program just says it cant play it and several other programs i cant even download because i just get an error message. i cant figure out how to listen to music or really do anything on here. So where do i start?

Thanks

---

### Post by nanotube on 2006-05-02
you can start by reading the guide that i linked to in my sig.
that will help you get your ubuntu system more usable, and teach you a few things in the process. :)
you should also check out the ubuntu wiki, (wiki.ubuntu.com)

---

### Post by Jeff Johnston on 2006-05-02
I program on Java a lot with my Ubuntu box. I know that Java is in the respositories, but I always just grab the JDK from Sun and install it myself. The place where you get the files on Sun have installation instructions. Get the files that are not RPM's. I also install the files right in my home user directory as it is just me on this machine.

Then in my .bashrc file (at the root of the user directory) I always put the reference to the JDK. This is a hidden file as you can tell because it starts with a dot. In Nautilus (file manager) you can do a View -> Show Hidden Files.

export JAVA_HOME=/home/jeff/j2sdk1.4.2_09
export PATH=$JAVA_HOME/bin:$PATH

export MAVEN_HOME=/home/jeff/maven-1.0.2
export PATH=$MAVEN_HOME/bin:$PATH

export ANT_HOME=/home/jeff/apache-ant-1.6.5
export PATH=$ANT_HOME/bin:$PATH


I also use Eclipse. For that just unzip and place where you want to. It seems that sometimes I have to put the command line argument to reference the JDK, and other times it just works. I guess it depends on how the Eclipse guys package it.

I think you may get multiple replys with different ways to install things, but this is what I do.

Hope that helps some. I have used Linux for quite a few years as my only desktop, but I remember being overwhelmed at first. Now many things come second nature, and I am hardly an expert...I just heavily rely on these forums :)

---

### Post by Nequeo on 2006-05-02
Check out this page: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) too

Will explain why you could not play that MP3, and how to fix the 'problem'.

Cheers,

---

### Post by nalmeth on 2006-05-02
> I am completly lost Then you have mosied to the right place, friend.
You look cold wet and tired from a hard linux introduction
[Automatix]("http://www.ubuntuforums.org/showthread.php?t=138405") should be able to cheer you up
Hope you get everything sorted out, enjoy

---

### Post by rahelvey on 2006-05-02
Automatix is excellant also look in the howto on the forums page and easy ubuntu got me up to speed in one afernoon. Being used to windoze then moveing to Linspire and my favorite Mepis which after my AMD fried last week I can no longer run, Ubuntu runs great on 800 intal box but is unlike anything I have played with before.
So as I said easy ubuntu got me started I finished up with automatix and now I can actually free hand download programs that I want.
Awsume system but aint plug in and play it os like Mepis or Linspire.
Ubuntu Rocks

---

### Post by rahelvey on 2006-05-02
Automatix is excellant.
In the how to on the forums page easy ubuntu got up to speed in a short time. This allowed me to be able and use automatix.
My AMD box fried last week. I personally love Mepis however it will not load on this old intell 800 box. Ubuntu loads and works perfect. However as you know I found it to be unlike anything I have ever played with.
After finding easy ubuntu then moving on to automatix I can now free hand down load programs I want. Ubuntu user since Saturday o4-29-06.
Ubuntu Rocks.:mrgreen: :D 8)

registered linux user 407613

---

### Post by ckonrad on 2006-05-02
[QUOTE=Nequeo]Check out this page: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) too

Will explain why you could not play that MP3, and how to fix the 'problem'.

Cheers,[/QUOTE]

Oh ok i didnt know that mp3 was a proprietary format i just thought it was a file type anyone could use to play music. I still havnt figured out how to play music though i have alot of music players installed, is there an internet radio that would work for ubuntu? I have tried xmms and that doesnt do anything, niether does rythmbox or juk or realplayer, my sound works fine though.

---

### Post by user1397 on 2006-05-02
To install *almost* anything, first use this guide ([https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)) to enable extra repositories, then use synaptic package manager (applications-->administration-->synaptic) to download a lot of software, around 17,000 or so.  you can also use the terminal to install programs (applications-->accessories-->terminal), by typing 
```
sudo apt-get install name_of_program
```
then after you feel more comfortable, you can download .deb, .tar and .rpm files manually from the web, and there's a special way to install each type. 
[B]WARNING: Installing software that's not from the repositories may harm your system! Be certain that the file is safe!

[/B]For a very complete guide on installing programs, read [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by rahelvey on 2006-05-03
As for radio stations I found that stream tuner serves to be the best yet on Ubuntu or should I say the easiest for noob to Ubuntu.
Once again I found it in easy Ubuntu.

---

