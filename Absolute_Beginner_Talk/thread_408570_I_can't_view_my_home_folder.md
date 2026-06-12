---
title: "I can't view my home folder"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-13
Hello,

I can't view anymore my home folder. Maybe that's because of I tried to replace current splash and entered an order in terminal s

udo cp /home/myfolder/my_new_image.png /usr/share/pixmaps/splash

Maybe that's the reason, maybe not. When I open home folder, there's absolutely nothing to see, which can't be true because  I saw in windows that there are the documents in this folder. Then, when I want to close it, I get the message:

The window "myname - file browser isn't responding

Forcing this application to quit will cause you to lose any unsaved changes" logging off and restarting doesn't help.

How can I turn everything back as it was before?

---

### Post by xopher on 2007-04-13
You might have screwed up some permissions, but that wouldn't explain the non-responsive window..

Try to chown the home folder back to you.. :

```
sudo chown -R username /home/myfolder/
```

where username is your user name and myfolder is your home folder.

---

### Post by O-pos on 2007-04-13
I tried and it didn't change anything.. :(

I forgot to say that when I try to close this window, get the above mentioned message and click quit, it closes and reopens again and so it lasts until I restart user or computer.. :(

---

### Post by xopher on 2007-04-13
Then it seems like a nautilus problem.. Can you browse around different directories without problems?

---

### Post by Patrick K on 2007-04-13
If you are running as Root, /home is a different directory than if you're running as a regular user. Try going to "File System > home > "your user name"". You should fine your home directory there. If you're not running as Root, I don't have any ideas.

---

### Post by O-pos on 2007-04-14
when I go to places>computer>file system there I can open all folders normally, even /home, which I can't open by places>home folder. however, then if I click on home/my-username-folder, it again gets frozen, pc resources usage jumps to maximum and the same happens what I already described above.

---

### Post by O-pos on 2007-04-15
So, noone's got an idea what to do? please advise something.. :(

---

### Post by Tundro Walker on 2007-04-15
I'm curious if maybe more than just the .png got copied to your **"/usr/share/pixmaps/splash"** folder.  First, since Nautilus seems to be hosed, open a terminal screen (which should open in your home directory) and type...

```
ls -a
```You should see all your home directory .<config> files show up.  If not, well, that's probably your problem.

From your same terminal, type...

```
ls -a /usr/share/pixmaps/splash
```You should only see a few files come up, all of which should be graphic files (.png, .svg, .jpg, etc...ignoring the . and .. since those are in every foldre).  One of those files should be your .png you moved.  If you see all kinds of .config files (EG: .bash-layout, .bash-history, etc) then you accidentally moved your home files to your "splash" screen directory.  If that's the case, you can try the following in your terminal...

```
cp /usr/share/pixmaps/splash/* /home/<your home folder name>
```That's a really sloppy way of copying everything over from the splash folder into your home folder (replacing "<your home folder name>" with the actual name of your home folder).  With that done, you can delete out the splash screen graphics that copied into your home folder, and you should be ok.

**Nautilus Borked...?**

However, if that doesn't seem to be the issue, it may well be Nautilus that's borked, like the other poster said.  Open Synaptic and mark "nautilus" for re-installation and apply.  Or, uinstall it and reinstall it.

---

### Post by O-pos on 2007-04-15
Thank you for the detailed inforamtion. I don't think that first issue should be my problem because after "ls -a" I saw that everything was in home directory what should be there. 

```
 ls -a /usr/share/pixmaps/splash 
```
only for files were there, all PNGs, so nothing seems wrong there

also, when  Iwant to open files contained in my home folder, it works fine when I open them with mplayer or Gimp (video files and images, respectiely)

maybe there's really nautilus problem? how can I reistall it with synaptic (I mean this issues with pesmissions and rights, which I don't understand well)?

---

### Post by Tundro Walker on 2007-04-15
Ok, before doing anything with Nautilus, let's just test to see if your user or super-user account is the one with the issue.

Open a terminal, and type

```
firefox
```...which will open firefox in user mode.  In the address bar, type...

```
/home/(your home folder)/
```...replacing (your home folder) with the actual name of your home folder.  You should see a list of files and folders, some of which are .(config) stuff.  You should even be able to to click on some of them (EG: .bash_history) to open it as view as text in FireFox.

If that works ok, then close Firefox, and in your terminal type...

```
sudo firefox
```...which opens it in super-user mode.  Once again, in the address bar, type in your /home/(your home)/ directory to surf there.  Again, you should see all kinds of files.

If either of these tests borked up, then either your user or super-user account has something wrong with its permissions, and you'll need to ask for someone else's help, because I'm pretty clueless how to solve those kinds of problems.

If they both seem to work fine, then it probably is Nautilus that's borked up, so we'll completely remove and reinstall it.

Hop into Synaptic...

[B]Main Menu > System > Administration > Synaptic Package Manager

[/B] ...click the "Search" button, and type in "nautilus" and enter.  This will bring up all kinds of stuff related to nautilus.  Look for the packaged named "nautilus", and right-click it's colored button, selecting "Mark for Complete Removal".

SIDE NOTE: You may get a message saying "ubuntu-desktop" will also get removed as a dependancy.  That's ok.  It's just a meta-file that ties together all the packages that are considered part of the Ubuntu desktop.  If, however, you see it's trying to remove tons of stuff, like Open Office, etc, then don't remove "nautilus" yet.  Instead, go to "ubuntu-desktop" and click to remove it (not complete removal, just remove).  Then apply that, which will remove the meta-package, and now you should be able to go back to "nautilus" and safely "complete removal" it without tons of other things getting removed, too.

With nautilus selected for complete removal, click "Apply", and it'll do its thing.  Then, if you removed the "ubuntu-desktop", you can go click it for re-installation, and it should select all the default Ubuntu packages to install, nautilus being one of them.  Or, just go select nautilus for installation again.  Click "apply" let it run, and you should have it back on.

Then, open a terminal and try...

```
nautilus
```This will open nautilus as a user, so surf to your home folder and test if your user rights let you see your home folder.  If it's ok (or not), then try...

```
sudo nautilus
```...which will open it as super-user, to which you surf to your home folder and see if you can see things ok.  

If things are still borked up for you after this, then I'm at a loss for what to do.

---

### Post by O-pos on 2007-04-16
Thanks for  the detailed information. With firefox they just work perfectly fine. I even followed folder tree and opened some files, everything's ok. One question before I start removing/reinstalling nautilus: My laptop is here nearby without boot CD and without internet connection (I'm using office PC right now). Is it still possible to dot that uninstall/reinstall thing with nautilus?

One more question: I have 4 png pictures in my usr/share/pixmaps/splash:

gnome-splash.png
splash-ubuntu2.png
ubuntu-slick.png
ubuntu-smooth.png

now gnome-splash.png is splash and I want to replace it with splash-ubuntu2.png ,how can I do that?

---

### Post by Tundro Walker on 2007-04-16
> **O-pos said:**
> One question before I start removing/reinstalling nautilus: My laptop is here nearby without boot CD and without internet connection (I'm using office PC right now). Is it still possible to dot that uninstall/reinstall thing with nautilus?

Ah, the lack of internet puts a damper on Synaptic and other Apt-Get related package managers (Aptitude, Adept, etc).  But, even if you can't hook your laptop to the net to ping online repositories, you should be able to use your install CD as a repository.  Check out this site here for more info about doing this...

[http://swik.net/Ubuntu/Only+Ubuntu/Package+Management+with+Synaptic+Package+Manager+in+Ubuntu/0p3b](http://swik.net/Ubuntu/Only+Ubuntu/Package+Management+with+Synaptic+Package+Manager+in+Ubuntu/0p3b)

Search for the words...

**Using CDs as offline package repositories**

...near the bottom of the article.  I'm pretty sure Nautilus is part of the main repository.  I'm also curious, since you can't hook the laptop onto the net, you may not have done any updates either.  That may be why Nautilus is messing up...there may have been a critical update released for it from the time you burned your install CD to now.  On your main PC (which I assume you're posting online with), you may want to d/l and burn the Ubuntu ISO again to get an up-to-date version.  Then use that to reinstall Nautilus.  The procedure should be just as I outlined before...using Synaptic to simply mark it for Complete Removal (so it's config files get bumped off, too), then using the Install CD as a repository to install it from again.


> One more question: I have 4 png pictures in my usr/share/pixmaps/splash:

gnome-splash.png
splash-ubuntu2.png
ubuntu-slick.png
ubuntu-smooth.png

now gnome-splash.png is splash and I want to replace it with splash-ubuntu2.png ,how can I do that?**Main Menu > System > Administtration > Login Window**

The 1st tab, called "Local", is where you can set your login / splash screen picture.  Ubuntu defaults to using a "Themed" Style, and there's various pre-built ones to choose from.  However, you can change it to "Plain" style, then check mark to use a Background image and other options.  You can surf your drive for your login splash screen...it doesn't necessarily have to be in the "splash" folder.  I made my login splash screen the same as my desktop, so the transition between the two is pretty seemless.  The only difference is the background color, because I used an .SVG image for splash & desktop that has transparent back letting background color show through.  (So, another tip there, you can use other image files then just .PNG....JPG, .SVG, etc)

However, I never see the login screen unless I'm switching session managers (IE: desktops, like going from Gnome to Fluxbox), because I set my auto-login on in the "Security" tab.  Just scope it out and mess around with the options.  Half the fun is just exploring the interface and screwing around with stuff.

---

### Post by Tundro Walker on 2007-04-16
I came across a "known bugs" sticky entry in the Ubuntu Forums.  One talks about a known bug in Edgy dealing with Nautilus using a lot of CPU...

[http://ubuntuforums.org/showpost.php?p=1747864&postcount=53](http://ubuntuforums.org/showpost.php?p=1747864&postcount=53)

It says there's a work-around.

---

### Post by O-pos on 2007-04-16
thanks for the link. I'll try at home to manage something with boot CD.

regarding splash,  I switched the login window to "plane" style and selected for the background image the same what I have as desktop wallpaper. I also enabled automatic login. But the splash screen (not login window) still appears and then true desktop wallpaper with other desktop elements appear. I'd like either to get rid of the splash, or change it to the other picture.. Changing of the image Login window>local>background didn't help.. :(

---

