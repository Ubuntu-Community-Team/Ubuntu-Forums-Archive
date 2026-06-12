---
title: "A Few Questions from a New User"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by anothrnbdy on 2007-11-03
Hi all,

I just installed Gutsy on my spare partition about a week ago. Since then I've run into some issues and figured this would be the best place to get help.

1) I'm taking Japanese classes, and I need to be able to type Japanese, including hiragana, katakana, and kanji. I've downloaded the language pack through the auto updater (really wish Windows would do this) but I have no idea how to switch between languages. 

2) This is just a small issue, but it bugs me a little, everything in Ubuntu seems a tad bigger than in XP. For Instance, my resolution is 1280x1024 and Firefox's fonts are about two sizes bigger than they are in XP and I can't fit as many tabs or bookmarks on the screen as I can in XP. I've noticed this throughout the OS and I don;t know how to unversally make everything a tad smaller, if such a way even exists.

3) This is a slight continuation of the above, but can I force Ubuntu to display a resolution higher than my LCD's native 1280x1024?

4) I cannot get playlists I've made in XP to play under any player in Ubuntu. This is after I populate the player's music library with the same folder hierarchy that I use in XP (all my music is on a separate, independent partition). Why is this and what can I do, if anything, to get them to work?

5) Finally, and this is probably not the place for it, I cannot get my google bookmarks under google toolbar to show. They are continually "being downloaded." How can I get these things to show up.

I know I'm forgetting something but oh well. Many thanks for the read and whatever advice you can give.
-Walter

---

### Post by defrex on 2007-11-03
For Japanese input, go to preferences>SCIM Input Method Setup. There you can find all the applicable settings, including keyboard shortcuts for changing the input method.

I've never noticed that problem of things being bigger in Ubuntu when going back and forth from Windows. But either way, there really isn't a quick way to make everything smaller (except the resolution, as you asked). In Firefox, CTRL+scroll will make the font smaller (or larger) on any given page. Also Preferences>Appearance you can change the gnome-wide font sizes. Other then that, the resolution can be forced be editing the file /etc/X11/xorg.conf. Be careful though, messing with that file can seriously mess up a system. Always keep a backup, and alway make sure you know how to restore the backup with only the command line.

As for google toolbar... I have no idea.

---

### Post by anothrnbdy on 2007-11-03
Thanks for the info. I don;t really wanna mess with config files, so I'll just get used to it.

One other thing I just remembered:

6) I have a Logitech G15 keyboard. Is there a way to get Ubuntu to recognize the LCD on the keyboard? A plug in or something? I would love to have the LCD clock going again. Also, I haven;t found any media players that recognize the media buttons (play, pause, next, ect), but do any exist?

Again, many thanks.
-Walter

---

### Post by gn2 on 2007-11-03
3) Yes, but the text will be unintelligible.

5) Have you considered using the Foxmarks add-on: [http://www.foxmarks.com/](http://www.foxmarks.com/)

---

### Post by anothrnbdy on 2007-11-04
Thanks, I had not ever heard of Foxmarks. The do the trick wonderfully. Many thanks.

---

### Post by jbizcocho on 2007-11-05
1> **anothrnbdy said:**
> Hi all,

I just installed Gutsy on my spare partition about a week ago. Since then I've run into some issues and figured this would be the best place to get help.

1) I'm taking Japanese classes, and I need to be able to type Japanese, including hiragana, katakana, and kanji. I've downloaded the language pack through the auto updater (really wish Windows would do this) but I have no idea how to switch between languages. 

2) This is just a small issue, but it bugs me a little, everythingPlay around with the Display settings, gnome font's etc.  You might find the combination you like indoing this rather than in dropping to the terminal and manually editing configuration files. in Ubuntu seems a tad bigger than in XP. For Instance, my resolution is 1280x1024 and Firefox's fonts are about two sizes bigger than they are in XP and I can't fit as many tabs or bookmarks on the screen as I can in XP. I've noticed this throughout the OS and I don;t know how to unversally make everything a tad smaller, if such a way even exists.

3) This is a slight continuation of the above, but can I force Ubuntu to display a resolution higher than my LCD's native 1280x1024?
**[FONT="Arial"]Play around with the Display settings, gnome font's etc.  You might find the combination you like indoing this rather than in dropping to the terminal and manually editing configuration files.[/FONT]**
4) I cannot get playlists I've made in XP to play under any player in Ubuntu. This is after I populate the player's music library with the same folder hierarchy that I use in XP (all my music is on a separate, independent partition). Why is this and what can I do, if anything, to get them to work?
[FONT="Arial"]**I'm assuming you have .mp3's you used in XP with your playlists.  the .mp3 format iis proprietary and so for legal reasons Ubuntu won't bundle it with the OS so you have to download it on your own.  The way I did it was an accident actually.  I figured out how get 7.04 to talk to my XP box I'm using as a server, and connected to a share with windows .avi files.  OK the first one I tried to play, totem said "no" and "do you want to try to search for the codecs?"  I said sure and when it finished finding and installing, I went and tested an .mp3 and it worked.  Certainly someone else here has a better solution but this worked for me :-)**[/FONT]

5) Finally, and this is probably not the place for it, I cannot get my google bookmarks under google toolbar to show. They are continually "being downloaded." How can I get these things to show up.

**[FONT="Arial"]I will say that though this is probably the most painful part, learning to do simple things on the command line is important.  I'll give you a short example.  I was looking for a way to improve the support for my trackpoint mouse on my keyboard(thinkpad T23) and found a "Joe Blow" page on the internet outlining steps claimed to be for 7.04.  I should know better but I stupidly copied and pasted the contents to xorg.conf and then saved.  I should have known this was bad because I had to go through so much to write the changes to the file.  Anyway I rebooted and sure enough I was greeted with a black screen and linux telling me to reboot once I'd fixed the bad lines in xorg.conf.  Long story short I had the good sense to copy the entire file to my /home directory in case the change didn't work, so I spent and hour on the command line figuring out how to copy and then rename the xorg.conf I backed up to the right folder.  Had I not known at least a small amount about the command line, I would be there now cursing my stupidity.  Lesson here, learn the command line BEFORE you get in a jam because you probably won't have the patience or time WHEN you get in a jam.[/FONT]**

I know I'm forgetting something but oh well. Many thanks for the read and whatever advice you can give.
-Walter

---

### Post by anothrnbdy on 2007-11-05
Thanks for the advice, Jbizcocho. I'm a CSE major and so I've done a little bit with the command line in UNIX, but pretty much exclusively for programming related stuff. 

As for the mp3 thing, I understand mp3 is a proprietary format. I've found players and codecs to play them. What I can't figure out is how to get play lists (.m3u) to work. Every player I've tried loads the play list like normal and then cycles through it as if it cannot find the songs. This is after I load the player's (Amarokk or XMMS or whatever) music library with the same file hierarchy I have under XP. I realize I may have to bite the bullet and redo all the playlists, but that's gonna take some time.

Anyways, thanks again for all the help.

---

### Post by ubuntu27 on 2007-11-05
> **anothrnbdy said:**
> 


1) I'm taking Japanese classes, and I need to be able to type Japanese, including hiragana, katakana, and kanji. I've downloaded the language pack through the auto updater (really wish Windows would do this) but I have no idea how to switch between languages. 




Hello Walter, welcome to the Ubuntu Community. Ubuntu commnity e youkoso. 

Here is a guide with screenshots on [How to imput Japanese in Ubuntu.]("https://help.ubuntu.com/community/SCIM")

[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

Good Luck!

---

### Post by mydrac on 2007-11-06
Hey:
for you second problem, maybe with change the configuration of the font directly  in firefox in the menu =>  Edit --> Preferences --> content. into this you find "font & colors". 

for you third problem, you can do this if you monitor support higher resolution: 
For do this things you have to be root. for be root you can start session as root or use the sudo command.

First do a backup of you  /etc/X11/xorg.conf
  > cp /etc/X11/xorg.conf /etc/X11/back_up_xorg.conf


Second open you xorg.conf and go to the *Section "Screen"* and add  to the line Modes the resolution that you want, i meaning:

you have something like this 
> Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Monitor genérico"
	DefaultDepth	24
        Option          "AllowGLXWithComposite" "true"
        Option          "RenderAccel" "true"
	SubSection "Display"
		Depth		1
		[COLOR="Blue"]Modes		"1280x1024" "1024x768" "800x600" "640x480"[/COLOR]
	EndSubSection
	SubSection "Display"
		Depth		4
		[COLOR="Blue"]Modes		"1280x1024" "1024x768" "800x600" "640x480"[/COLOR]
	EndSubSection
	SubSection "Display"
		Depth		8
		[COLOR="Blue"]Modes		"1280x1024" "1024x768" "800x600" "640x480"[/COLOR]
	EndSubSection
	SubSection "Display"
		Depth		15
		[COLOR="Blue"]Modes		"1280x1024" "1024x768" "800x600" "640x480"[/COLOR]
	EndSubSection
	SubSection "Display"
		Depth		16
		[COLOR="Blue"]Modes		"1280x1024" "1024x768" "800x600" "640x480"[/COLOR]
	EndSubSection
	SubSection "Display"
		Depth		24
		[COLOR="Blue"]Modes		"1280x1024" "1024x768" "800x600" "640x480"[/COLOR]
	EndSubSection
EndSection

don't have to be exactly the same depend of you hardware but for my works of this way. 
So that you have to do is add the resolution that you want, if i want put *_1360x768_* (that it's the next resolution after 1280x1024 so i put in the line "Modes"  this resolution and the line change to 
> [COLOR="Blue"]Modes		[COLOR="Red"]"1360x768"[/COLOR] "1280x1024" "1024x768" "800x600" "640x480"[/COLOR]
Then restart the X and automatically your resolution of  "1360x768" should work ( i repeat, you monitor have to support this resolution if not  automatically charge the max resolution that support). You can see in the menu of the screen the gnome  if you have the resolution that you add, ( i dont know where are this menu because i don't use gnome.)

*  In this [page]("http://www.latenighthacking.com/projects/monitorResolutions.html") you find the different resolution that could be used in the monitors.
*  For restart the X hit  "ctrl + alt + back space".

for you fifth problem i use a [google bookmarks button]("https://addons.mozilla.org/en-US/firefox/addon/2453") and works great.

---

