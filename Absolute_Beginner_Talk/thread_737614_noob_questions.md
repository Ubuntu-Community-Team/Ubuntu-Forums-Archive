---
title: "noob questions"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by R0Y_G_B1V on 2008-03-27
Alright, so, 18 yr-old looking for a better OS than Vista/XP for college. Figured I would dual-boot on an Ubuntu dell laptop or System76. Right now I've installed Ubuntu on an external 80GB drive on my desktop at home to try and learn how to use it properly before going out in the real world. So far I love it, and it's fairly simple in my opinion, I'm also fairly intelligent when it comes to computers, grew up on them, and can usually figure out stuff just by experimenting. ANYHOW, some LAME problems I'm having....

1.) Do not understand how to download anything on the net, such as finding the correct files within the .zip I get. Take for example Firefox2, I couldn't figure out how to actually find the browser and run it from the .zip I got. Yes I extracted it. I had to resort to a terminal tutorial I found to do it. I don't want to do this for everything I download.

2.) Amarok? This thing isn't living up to the hype. Or maybe I'm stupid. I don't need an iPod thing, just something that I can search for any songs, all I can see that I can do is seach from within a genre, considering I like techno, there isn't much in there!! Any way I can search for a song by title or is there a better program than Amarok for that?

3.) If any of you want to throw in their 2 cents on my situation I would be glad to hear it, I'm def. not running windows as my main OS thru college, either Mac or Ubuntu. I know the Ubuntu community rocks =)

---

### Post by POW R TOC H on 2008-03-27
> **R0Y_G_B1V said:**
> Alright, so, 18 yr-old looking for a better OS than Vista/XP for college. Figured I would dual-boot on an Ubuntu dell laptop or System76. Right now I've installed Ubuntu on an external 80GB drive on my desktop at home to try and learn how to use it properly before going out in the real world. So far I love it, and it's fairly simple in my opinion, I'm also fairly intelligent when it comes to computers, grew up on them, and can usually figure out stuff just by experimenting. ANYHOW, some LAME problems I'm having....

1.) Do not understand how to download anything on the net, such as finding the correct files within the .zip I get. Take for example Firefox2, I couldn't figure out how to actually find the browser and run it from the .zip I got. Yes I extracted it. I had to resort to a terminal tutorial I found to do it. I don't want to do this for everything I download.

2.) Amarok? This thing isn't living up to the hype. Or maybe I'm stupid. I don't need an iPod thing, just something that I can search for any songs, all I can see that I can do is seach from within a genre, considering I like techno, there isn't much in there!! Any way I can search for a song by title or is there a better program than Amarok for that?

3.) If any of you want to throw in their 2 cents on my situation I would be glad to hear it, I'm def. not running windows as my main OS thru college, either Mac or Ubuntu. I know the Ubuntu community rocks =)

Alright, so your age really doesn't matter to your OS, it won't mind at all.
And yes, it's quite typical that people think that every problem they can't solve is 'LAME'
1.) Try learning a bit about bash, and lean how to use some simple programs, first. You probably have a source code, you need to enter the folder (via Terminal), and type $./configure
then, when that's done, if it displays any missing files, type :
$sudo apt-get install [name of the missing file]
if it goes OK, type
$make
This command actually compiles the source, with options determined by 'configure' script.
After that is done (can take a while) type :
$sudo make install
That one 'installes' the files...

2.) Try the default rhythmbox.
3.) What are you talking about?

---

### Post by spiderbatdad on 2008-03-27
1.) Most generally the repositories and synaptic package manager are your primary software sources. Beyond that .deb packages are the easiest to handle. A zip file would entirely depend on the contents, as to whether there was anything you could run in it. This link gives a general overview of installing software: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

2.) I like Banshee, but use rhythm box also.

3.):)

---

### Post by R0Y_G_B1V on 2008-03-27
Okay then, way to be blunt. And if you didn't get the #3 then please don't respond, perhaps you're not english? 

And I just said I didn't want to go through terminal commands to install everything, so why did you list commands anyhow?

Thanks at least for the musicbox idea, except I tried that obviously it being a default program.

Anyone else?

---

### Post by Blue_Lander on 2008-03-27
> **R0Y_G_B1V said:**
> 
1.) Do not understand how to download anything on the net, such as finding the correct files within the .zip I get. Take for example Firefox2, I couldn't figure out how to actually find the browser and run it from the .zip I got. Yes I extracted it. I had to resort to a terminal tutorial I found to do it. I don't want to do this for everything I download.

Keep in mind that many common applications can be found in the Synaptic Package Manager, and even more can be found if you enable the extra repositories. 

Installing things in Linux was a pain for me when I started too, but you get used to it quick. If you check the package manager whenever you want to download something, you'll probably be pleasantly surprised how often its in there. 

Good luck! :)

---

### Post by R0Y_G_B1V on 2008-03-27
> **spiderbatdad said:**
> 1.) Most generally the repositories and synaptic package manager are your primary software sources. Beyond that .deb packages are the easiest to handle. A zip file would entirely depend on the contents, as to whether there was anything you could run in it. This link gives a general overview of installing software: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

2.) I like Banshee, but use rhythm box also.

3.):)

Thanks I guess. I just don't get which file type would be the actual exectutable program within what I download.

---

### Post by spiderbatdad on 2008-03-27
> **R0Y_G_B1V said:**
> Thanks I guess. I just don't get which file type would be the actual exectutable program within what I download.

.bin

---

### Post by R0Y_G_B1V on 2008-03-27
> **spiderbatdad said:**
> .bin

Oh...thanks, a lot.

---

### Post by smurphy_it on 2008-03-27
As stated the repositories are your first thing to go to download programs.  If you are running ubuntu, it comes with the synaptic package manager.  System, Administration, synaptic package manager.

It's a gui so it is pretty easy to figure out.  There is a search button there as well.  So for example you were looking for CD/DVD burning programs, you could just type in burning, and after a little bit it will give you a list and a description of each one.  Also, if you click in the right hand side where the programs are listed, and wanted something which started with the letter k, just start typing, it will automatically bring you there via letter.

Xmms is a music player like Winamp.  Rythmbox is default in ubuntu.  There are a few others out there, I just can't remember their names off top of my head.

As for installing programs.  If you download a .deb file, when you open it, the dpkg manager will take care of installing the program and all dependencies for you.  

For example, goto [www.getdeb.net](www.getdeb.net) and have a look there.

Generally the package managers or .deb files are the way to go, because with a couple of clicks or keystrokes you can have a program installed.

For example.

Open a terminal and type sudo apt-get install mozilla-thunderbird and that will install the email program for you, without having to download the source, and go through the process of compiling and installing it.

---

### Post by POW R TOC H on 2008-03-27
> **R0Y_G_B1V said:**
> Okay then, way to be blunt. And if you didn't get the #3 then please don't respond, perhaps you're not english? 

And I just said I didn't want to go through terminal commands to install everything, so why did you list commands anyhow?

Thanks at least for the musicbox idea, except I tried that obviously it being a default program.

Anyone else?

Sorry, no offense ment. I'm always a blunt a-hole. Anyway, you're going to have to learn about terminal sometime, and trust me- it might sound boring, but once you get a hang of it... It's amazingly powerful.

If you decide to learn bash sometime in the future, here's a good start :
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)
As for amarok, I didn't find it that good either...

And yes, if you like to learn by experimenting, linux is the right OS.

---

### Post by ubuntu-freak on 2008-03-27
> **R0Y_G_B1V said:**
> And I just said I didn't want to go through terminal commands to install everything, so why did you list commands anyhow?

 
As others have said, you don't need the Terminal to install applications, but you will need it for some tasks (new encrypted DVDs playback, manually installing Adobe Flash, optimizing and editing configurations etc), this is Linux afterall, and it's a very powerful tool anyway. 
 
Have you tried Exaile? It's a fork of Amarok, not sure if it has a better search function though. Search Synaptic for music players and see which one you prefer.
 
Nathan

---

### Post by twright on 2008-03-27
downloading programs from websites is really a windows thing :KS

in linux you generally just need to click on add/remove programs in the applications menu and you can choose from a huge list of programs which have been verified (so you can't download spyware from there) and will be automatically updated. however there are a few exceptions and you can download them as a .zip/tar/bz2 and you just need to right click and extract to whereever you want them (you home folder is usually a good place). some programs provide automated installers as .bin, you may need to right click and select properties so you can allow to installer to be ran (in linux for someting to be ran as a program it needs permission, yet another reason you are safe from virii)

don't feel compelled to learn bash, if you do you will be able to do stuff a lot faster but it is not necessary to learn it just to use ubuntu.

for music i just use rhythmbox, it's nice and simple + it has some great features

i think that ubuntu is a much better choice than OSX as with ubuntu pretty much every piece of software you will ever need you can get free (and it's often higher quality as well) but with both OSX and windows you have to pay for even basic functionality such as an office suite

---

