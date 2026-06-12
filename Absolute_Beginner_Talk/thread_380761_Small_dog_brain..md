---
title: "Small dog brain."
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-03-10
I just transfered from Windows Xp to Ubuntu, and I've got some questions. Since I'm Linux-illiterate, I would like you people to talk to me as if your talking to a small dog.

 Question #1: How can I customize my screen size? I'm using an Nvidia Gefore FX 5200 with a rather new monitor, so I know it can handle it, but when I try to set it to 1280 x 768, the option is not available. I've heard that you could customize the resolution and refresh rate, but I need... simplified... instructions.

 Question #2: How do I run .run files? I know that there scripts, but again, I need simple instructions.

 Question #3: Is there a firewall that I could download for Ubuntu? If one is installed by default, how can I configure it?

 Question #4: I've only been using Ubuntu for a few hours, and I'm already getting tired of the Orange. How can I change the theme? Remember, talk to me as if I were a small dog...

 There will be more questions, but I can't think of anything else to ask.

 Thanks-
            ZeroWing

---

### Post by o_fortuna on 2007-03-10
1: This is a bit unfortunately conplicated to do. The most reliable way to select resolutions is to open up a terminal (Applications--Accessories--Terminal) and type in
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This will give you an ugly blue thingy that you have to navigate with the keyboard. Just press enter to accept default option for the graphics driver. Then when it gives you a list of resolutions, select the resolution you want and press SPACEBAR to make a little star appear next to it. Then press enter.

Once you're done with that, just log out and press Ctrl+Alt+Backspace. Hopefully that won't break anything, and it will work.

2. To run .run files which are stored in your Home directory, open up a terminal (Applications--Accessories--Terminal) and type
```
./name.run
```
Where name.run is the name of the run file. Notice the ./ part. It's important; it tells the computer to run it.

3. Open up Applications--Add/Remove and search for Firestarter. Install it, and it will appear probably under System--Administration (sorry, don't remember exactly where). Select it to start the simple configuration. You can probably mostly just click next. If you restart the computer, the firewall will run, even if the GUI icon doesn't appear on your desktop.

4. System--Preferences--Theme. Select one you like, or go to [http://www.gnome-look.org]("http://www.gnome-look.org") to find more.

Hope that helps.

---

### Post by Madpilot on 2007-03-10
> **ZeroWing said:**
> I just transfered from Windows Xp to Ubuntu, and I've got some questions. Since I'm Linux-illiterate, I would like you people to talk to me as if your talking to a small dog.

 Question #1: How can I customize my screen size? I'm using an Nvidia Gefore FX 5200 with a rather new monitor, so I know it can handle it, but when I try to set it to 1280 x 768, the option is not available. I've heard that you could customize the resolution and refresh rate, but I need... simplified... instructions.


I assume you found System -> Preferences -> Screen Resolution and that's what doesn't list your res?

I've never had resolution troubles, so I'm not sure what to suggest. The solution will probably involve editing xorg.conf manually, though. I'll let more experience folks finish this one.

> 
 Question #3: Is there a firewall that I could download for Ubuntu? If one is installed by default, how can I configure it?

Unlike XP, Ubuntu has no active services by default; a firewall isn't as needed. That said, there is one running in the background by default; if you want a graphical app to control it, install Firestarter. Firestarter has good documentation, and a number of helpful wizards for various common things.

> 
 Question #4: I've only been using Ubuntu for a few hours, and I'm already getting tired of the Orange. How can I change the theme? Remember, talk to me as if I were a small dog...

System->Preferences->Theme

Installing more themes is also easy; have a look at [https://help.ubuntu.com/community/UbuntuEyeCandy]("https://help.ubuntu.com/community/UbuntuEyeCandy") for more information.

---

### Post by Patrick K on 2007-03-10
You didn't say what desktop so I'll go with Gnome. The default Ubuntu desktop.

Q1) The best bet for screen size is to install the nvidia drivers. The easiest way to do this is to use the Envy script. You can find it here:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Once the drivers are installed, you will find the NVidia control applet in Applications->System Tools. My old Geforce 2 MX card has resolutions up to 1920x1200 available. 

Q2) Can't help

Q3) Linux has a built in firewall called iptables, You can download a graphical frontend for it in Synaptic Package Manager (System->Administration) 

Q4) Go to System->Preferences and select Theme.

---

### Post by mahy on 2007-03-10
> **ZeroWing said:**
> Question #1: How can I customize my screen size? I'm using an Nvidia Gefore FX 5200 with a rather new monitor, so I know it can handle it, but when I try to set it to 1280 x 768, the option is not available. I've heard that you could customize the resolution and refresh rate, but I need... simplified... instructions.

Everything is in the file named /etc/X11/xorg.conf. First make a backup of it (in Terminal): 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bckp
```

Then edit it:

```
sudo gedit /etc/X11/xorg.conf
```

After a few seconds' reading you'll see a line with resolutions specified. Delete things like "800x600" and put there your desired resolution. However, 1280x764 sounds really weird. I'd say it's either 1280x800 or 1280x1024.

> 
 Question #2: How do I run .run files? I know that there scripts, but again, I need simple instructions.


Open the Terminal and run 'chmod +x [filename]' to make it executable and then './[filename]' or 'sudo ./[filename]' to run it.

> 
 Question #3: Is there a firewall that I could download for Ubuntu? If one is installed by default, how can I configure it?


There is! Open the terminal and run:

```
apt-get install firestarter
```

> 
 Question #4: I've only been using Ubuntu for a few hours, and I'm already getting tired of the Orange. How can I change the theme? Remember, talk to me as if I were a small dog...


About as easily as you'd do it on windows. But i don't use Gnome (your desktop environment) so i can give you no advice.

If in doubt, please check [www.psychocats.net](www.psychocats.net) for help and tutorials.

---

### Post by ZeroWing on 2007-03-10
Wow... quick responses... Only problem now is that I can't seem to get the Add/remove thingy to run properly. It pops up, loads some things, then closes itself. Any way I could fix that?

---

### Post by ZeroWing on 2007-03-10
> **ZeroWing said:**
> Wow... quick responses... Only problem now is that I can't seem to get the Add/remove thingy to run properly. It pops up, loads some things, then closes itself. Any way I could fix that?


 Forgot to mention that Firestarter doesn't seem to want to download, either. I tried to set up Synaptic to the universe repository, but It seems to keep on reverting back to it's default settings. Can anyone help with this?

---

### Post by RomeReactor on 2007-03-10
Hi. How are you setting Synaptic up with the repositories? An easy way to do it would be to open Synaptic, click on "Settings-->Repositories" and check all the appropriate boxes there (in your case, universe). Then click on the blue "Reload button and you should be good to go.

> I would like you people to talk to me as if your talking to a small dog.

All of us were/are new to linux at some point or another; we are here to help you with your problems, and there's no such thing as a dumb question. So ask away, and we'll do our best to help you solve your issues! =)

---

### Post by happy-and-lost on 2007-03-10
With regards to theming, if you find a theme you like on gnome-look, the easiest way to install it is to drag and drop the *.tar.gz (this is sort of like a .zip... just not ;)) into the theme manager. It should tell you it's installed. If you click on the "Customise" button in the theme manager you can choose the combination of theme, window border and icons you like. See [this thread]("http://ubuntuforums.org/showthread.php?t=373055") for some theming inspiration.

And, welcome to Ubuntu :guitar:

---

### Post by ZeroWing on 2007-03-10
> **RomeReactor said:**
> Hi. How are you setting Synaptic up with the repositories? An easy way to do it would be to open Synaptic, click on "Settings-->Repositories" and check all the appropriate boxes there (in your case, universe). Then click on the blue "Reload button and you should be good to go.


 I'm doing that, then I click cancel on the properties menu. I click on it again, and it's unchecked.

 Also, Add/remove programs tool doesn't work.

---

### Post by ZeroWing on 2007-03-10
And another thing: I get an error when I try to install anything with apt-get:

 E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

 I don't remember installing a user by the name of Root... My user is an administrator, but that doesn't seem to be enough.

---

### Post by ragadanga63 on 2007-03-10
try "sudo apt-get install firestarter" (without the quotation marks).

be ready with your log in  password

---

### Post by ZeroWing on 2007-03-10
I got mostly everything figured out now. Thanks all.

 ...I'm glad that the makers of Ubuntu installed/made Synaptic...

---

### Post by ZeroWing on 2007-03-10
Another problem...

 I'm trying to install an Nvidia driver for my... Nvidia video card... but when I download it, I get a .run file. This would be fine, if I could get the thing to work. Every time I click on it, Gedit pops up to tell me that it cannot recognize the file. When I try to open it the way Mahy said I could, the terminal says that the directory does not exist.

 Can anyone help with this?

---

### Post by Patrick K on 2007-03-10
Why don't you run the Envy script I suggested earlier. Works great and automates the installation for you. Keep the script installed since many updates will fry the current driver install and you need to install again.

---

### Post by ZeroWing on 2007-03-10
> **Patrick K said:**
> Why don't you run the Envy script I suggested earlier. 

 I can't manually install that! I've just came from WinBlows! How do you install it? What file do you click?

---

### Post by Patrick K on 2007-03-11
The instruction for installing and running are on the page. The first FAQ question. 

The link you click on is:
envy_0.9.1-0ubuntu2_all.deb
(Not here but on the page.)
Go for it!

---

### Post by ZeroWing on 2007-03-11
> **Patrick K said:**
> The instruction for installing and running are on the page. The first FAQ question. 

The link you click on is:
envy_0.9.1-0ubuntu2_all.deb
(Not here but on the page.)
Go for it!

 Oh... Heh... I knew that.

 Seriously.

 Thanks.

---

### Post by steveneddy on 2007-03-11
> **ZeroWing said:**
> 

 Question #4: I've only been using Ubuntu for a few hours, and I'm already getting tired of the Orange. How can I change the theme? Remember, talk to me as if I were a small dog...



woof!! bark bark!! growllll!!

Sorry, couldn't resist. Go [here ]("http://www.gnome-look.org/")to find theme's, wallpaper, icon themes, logon themes, just about anything you will want to customize the look of Gnome. 

Also you may look [here]("http://art.gnome.org/").

Hope that this helps.

---

### Post by steveneddy on 2007-03-14
> **ZeroWing said:**
> I can't manually install that! I've just came from WinBlows! How do you install it? What file do you click?

Whoa! was I that bad when I started?

maybe I thought those things.....

I'm glad that you are learning - some people get this far along in a post and give up.

You will be rockin' along in no time.

---

