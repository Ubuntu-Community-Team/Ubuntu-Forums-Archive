---
title: "Wishing I could push print screen in Xubuntu to take screen shot like in Ubuntu."
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-05
What application is it that Ubuntu comes with that allows it so that right when I push the "print screen" button it immediately takes a screen shot and asks me where I'd like to save it? I saw a few others while I was googling around but they seemed to involve a lot of tweaking and configuring. I wish I just had what Ubuntu has so that I can just push the print screen button so that I may take a screen shot.

---

### Post by Flying caveman on 2008-03-05
I thought it had that feature somewhere,  you could always install gimp and use its screen capture feature.

or read this for some other ideas. [http://ubuntuforums.org/showthread.php?t=246737](http://ubuntuforums.org/showthread.php?t=246737)

---

### Post by jken146 on 2008-03-05
[http://ubuntuforums.org/showthread.php?t=639081&highlight=screenshot](http://ubuntuforums.org/showthread.php?t=639081&highlight=screenshot)

---

### Post by stchman on 2008-03-05
> **whoscheesemine said:**
> What application is it that Ubuntu comes with that allows it so that right when I push the "print screen" button it immediately takes a screen shot and asks me where I'd like to save it? I saw a few others while I was googling around but they seemed to involve a lot of tweaking and configuring. I wish I just had what Ubuntu has so that I can just push the print screen button so that I may take a screen shot.

Hit ALT-Print Screen and Ubuntu will pop up and ask you where to save the image.  Alt-Print Screen does the active window, Print Screen by itself does the entire desktop.

---

### Post by whoscheesemine on 2008-03-05
> **stchman said:**
> Hit ALT-Print Screen and Ubuntu will pop up and ask you where to save the image.  Alt-Print Screen does the active window, Print Screen by itself does the entire desktop.

Yeah.... I know that..... it most deffinitely does in UBUNTU however, I am using XUBUNTU, I'm wondering what app it is that Ubuntu has installed, that Xubuntu does NOT have installed that allows it so that as soon as I press the print screen button it immediately asks me where I would like to save it.

---

### Post by jw5801 on 2008-03-05
The command gnome uses is gnome-printscreen (I think, there might be another hyphen in there). Type that into a terminal and it'll tell you if it's installed, or if it isn't it'll tell you what package it's in so you can install it.

EDIT: Sorry, gnome-screenshot is the command.

---

### Post by kerry_s on 2008-03-05
there's xfce4-screenshooter-plugin
check if it's installed.

i think i use to use scrot and had to put the keyboard shortcuts my self.

anyways here's what i use now with scrot(sudo apt-get install scrot):
scrot %T.png;xmessage -timeout 2 "screen shot done" <full screen, i use print
xterm -g 35x0+0+0 -e scrot -sb %T.png <select, i use ctrl+print
xterm -g 10X0+0+0 -e scrot -dc 5 %T.png <wait 5, i use alt+print

---

### Post by santiagoward2000 on 2008-03-05
The command that Ubuntu uses is **gnome-screenshot**. If you want to install it, it's part of the **gnome-utils** package.
Personally, I use **scrot** in my Xubuntu. It's a command line application for taking screenshots, and can be customized with lots of variables.
Cheers!

_EDIT:_
Just in case you want to use **scrot**, to set it with the PrtSc key, go to **Applications/Settings/Keyboard Settings**. Select the **Shortcuts** tab, click on **Add...** and add any name you want. Then click on the other **Add** button (under the commands list), enter the **scrot** (+ all the variables you want) and then press the key.
If you want to see all the variables, enter **scrot -h** on a terminal.

---

### Post by whoscheesemine on 2008-03-06
> **santiagoward2000 said:**
> The command that Ubuntu uses is **gnome-screenshot**. If you want to install it, it's part of the **gnome-utils** package.
Personally, I use **scrot** in my Xubuntu. It's a command line application for taking screenshots, and can be customized with lots of variables.
Cheers!

_EDIT:_
Just in case you want to use **scrot**, to set it with the PrtSc key, go to **Applications/Settings/Keyboard Settings**. Select the **Shortcuts** tab, click on **Add...** and add any name you want. Then click on the other **Add** button (under the commands list), enter the **scrot** (+ all the variables you want) and then press the key.
If you want to see all the variables, enter **scrot -h** on a terminal.

Awesome thanks alot.

However, this brings me to a new dilema that I was wondering if any of the contributors or passby's might be able to help me with.


  #1   Report Post  
Old 1 Minute Ago
whoscheesemine whoscheesemine is online now
Just Give Me the Beans!
	  	
Join Date: Jan 2008
Beans: 69
Thanks: 22
Thanked 0 Times in 0 Posts
Trying to keep system resource usage low... should I install gnome-utils or scrot?
I'm trying to keep system resource usage to a bare minimum on a certain Xubuntu install I have on a machine with only 384MB RAM installed (although it only says I have 376MB RAM I have an idea why but i'll save that for another thread) I'd like to have it so that when I press print screen it will automatically take a screen shot and either ask me where to save it or dump it to a preset location. The two choices I've come accross are to use either scrot or the "gnome-screenshot" command. The only way I can use the "gnome-screenshot" command is if I have gnome-utils installed. Now, I'm no Ubuntu/Linux pro (far from it actually), but I'm sure that some process has to be running for me to either use the scrot or gnome-utils capabilities. Processes use system memory and as I stated before the goal is to use as little as possible. So, I ask ye learned users of the Linux environment which one will yield the least amount of system memory so that I may keep a smooth running PC in my little brother's bedroom with out hearing the constant screaming of "I WANT WINDOWS BACK!"


The following is completely irrelevent to my prior post:

It just came to my attention that after reading the last statement of my post that you may have thought to yourself. Dude, if your family wants Windows back why don't you just give it back to them? Well, although the members of my family use this computer on a daily basis, none of them have taken the time to try to understand how this box works whatsoever. So, basically, anytime anything goes wrong with it they run to me, no matter what I'm in the middle of, and expect me to spend a night to a few days, cleaning up after them. Not to mention XP should never be ran on a computer with only 256MB RAM to begin with. I figure it would be much easier to completely tweak this Xubuntu system to meet their every need, so that I can finally sit back, relax, and never have to touch this damn box ever again. I've almost got them completely converted except on a couple little aspects I'm tweaking with, and one of them involves me taking a screen shot for better visual aid, which brings me to this post.

---

### Post by hyper_ch on 2008-03-06
I found a little script using imagemagick that enabled screenshots for me.

---

### Post by whoscheesemine on 2008-03-06
> **hyper_ch said:**
> I found a little script using imagemagick that enabled screenshots for me.

Care to elaborate?

---

### Post by hyper_ch on 2008-03-06
[http://gentoo-wiki.com/TIP_Make_a_Screenshot_with_PrintScreen_Key](http://gentoo-wiki.com/TIP_Make_a_Screenshot_with_PrintScreen_Key)

Use the script provided in there and install imagemagick. Make the script executable and move it to the according directory... then in your keyboard setup you can assign a key for making the screenshot

---

### Post by santiagoward2000 on 2008-03-06
> **whoscheesemine said:**
> Trying to keep system resource usage low... should I install gnome-utils or scrot?

I'd say **scrot** is lighter. **gnome-utils** comes with other applications (like a dictionary or a file search) that you may not want to have.

---

### Post by whoscheesemine on 2008-03-06
> **santiagoward2000 said:**
> I'd say **scrot** is lighter. **gnome-utils** comes with other applications (like a dictionary or a file search) that you may not want to have.

Do you mean lighter on RAM or Hard Drive space? Hard drive space isn't really an issue, I'm just trying to use as little RAM as possible.

---

### Post by santiagoward2000 on 2008-03-06
> **whoscheesemine said:**
> Do you mean lighter on RAM or Hard Drive space? Hard drive space isn't really an issue, I'm just trying to use as little RAM as possible.

I meant HD space. I don't really know about RAM. My guess is that **scrot** would be lighter, because it doesn't open a new window asking you for the name and location the file will be stored in, but I have no numbers to compare.
Sorry!

---

### Post by whoscheesemine on 2008-03-06
> **hyper_ch said:**
> [http://gentoo-wiki.com/TIP_Make_a_Screenshot_with_PrintScreen_Key](http://gentoo-wiki.com/TIP_Make_a_Screenshot_with_PrintScreen_Key)

Use the script provided in there and install imagemagick. Make the script executable and move it to the according directory... then in your keyboard setup you can assign a key for making the screenshot

yeah that one's not really working for me

after I installed it, it said to make sure X and png USE flags are enabled

how? it never mentioned how to do it, nor did it link me to tell me how to do it, i used app finder and desktop search to look for this program and I can't find it anywhere, I even typed imagemagick into the terminal by its self and it said bash: command not found

so i figured okay i'll just go on and use the terminal commands it gave me

so the first one is:

```
# emerge -av imagemagick
```

I entered that one and.... nothing that's okay though, I've entered commands that do things before even though nothing is said back to me

so I decide to enter the next code it gives me figuring it MUST do something

```
$ import screenshot.png
```

yeah the only thing that gave me was this:

bash: $: command not found

does perhaps the fact that I'm using Xubuntu have anything to do with this incompatability? I think I'm going to go with Scrot... I am still curious as to what's up here though.

If anyone knows the terminal commands to actually create a screen dump I will gladly write a script with it and map it to a key, as I'm trying to use a little system resources as possible.

PS: just a thought... is emerge some program that I need for this to work? I admit I'm a noob.

[COLOR="Red"]Edit:[/COLOR] I found a much better description and a guide that talks of multiple ways of takeing screen dumps. Thanks to everyone who contributed.

[http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux](http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux)

---

### Post by jw5801 on 2008-03-06
The "#" and the "$" are meant to symbolise command prompts, I assume. "#" in a command is actually a comment, anything after it will be ignored. So, yes the first command really didn't do anything. The "$" isn't anything at all, so bash is telling you it can't find the command "$". Try running the commands without those at the start and it should work a little better.

---

### Post by whoscheesemine on 2008-03-06
To anyone else who may find themself wondering to this page in search of the same thing I was searching for. Here's the route I decided to take:

Imagemagick is actually really cool. For those of you who are concerned about their system resource usage, from what I've checked it doesn't seem to use any of your RAM when it comes to taking a complete full window screen shot (it does however use a breif spilt second 7% of your CPU), and I've mapped the following command to my "print screen" button:

```
 import -window root MyScreenshot2.jpg
```

You can use just about any file format, I just chose jpg because its the smallest photo format I know of that picture uploading sites allow you to use.

I also mapped this command to my ctrl + "print screen"

```
import MyScreenshot.jpg
```

This command almost uses 800kb of Memory I noticed, but that's like next to nothing and is only temporary. It turns your mouse into a little 'X' and gives you the ability to make a stretchy box in which the contents will be screen dumped.

Thanks to everyone who posted.

---

