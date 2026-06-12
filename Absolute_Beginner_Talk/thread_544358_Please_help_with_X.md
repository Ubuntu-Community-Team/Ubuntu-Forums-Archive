---
title: "Please help with X"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Sprogg2001 on 2007-09-06
I have royally screwed my x configuration! 

I have been trying to set my screen res to 1200x676 I have a Nvidia 7600 installed with nv drivers and have been following the instructions on different threads to configure x

 Im now so confused I dont know where to turn. I have over 9 x files in my etc\X.11\ folder so I dont know which one is being used I have changed all of them none get me to the correct resolution, most of the time I cant see more than half the screen so it hasn't been easy. 

Can anyone please explain how I get rid of all the modified x files and just change the one so I end up with the right resolution. I hate to say it but this is so straight forward in windows why is it so difficult in Kubuntu?

  :confused:

---

### Post by southernman on 2007-09-06
First off, it's as difficult as you make it... k :p

Now, boot into recovery mode and login on the console.

cd to "/etc/X11"

do "ls"

"sudo rm -f xorg.conf1 xorg.conf2" until you have them all listed and hit enter

do "ls" again to make sure they are gone

now do "sudo dpkg-reconfigure xserver-xorg" don't not stop this process as you've just deleted all your xorg.conf files per your request. 

When finished with the reconfiguration, do "sudo shutdown -r now"

/edited - apologies for my opening remark. It's been a long day and I'm getting punchy. I do hope you get this squared away. I'll check back after some rest to see how you progress.

---

### Post by henriette_holm on 2007-09-06
The one being used is the xorg.conf - the other 9 must have different names, right? It's always a good idea to do a copy of the file before editing. Something like:

cp xorg.conf ~/backup/xorg.conf_old


Then you can always copy it back, if you mess up the file. Anyway, post your problem, hardware etc. here and somebody will properly be able to help you.

/Henriette

---

### Post by Sprogg2001 on 2007-09-06
Ok, thank you for the replies 

I have done as asked asked deleted all xconfig files a reconfigured xserver.xorg from recovery mode I have selected the resolution modes to display and provided my Hz Vz modes 

I then edit the xorg.conf file to input my desired resolution the end result of this is below
[B]
Section "Monitor"
	Identifier	"Sony Bravia EU"
	Option		"DPMS"
	HorizSync	31-60
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia"
	Monitor		"Sony Bravia EU"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1200x676"
	EndSubSection
EndSection[/B]

and then I restart X 

only to find it hasnt worked, and its now using 1280x720 @ 50 hz and one inch of the screen on ether side cannot be seen. when it should be using 1200x676 @ 60 hz

any ideas, what did I do wrong? :mad:

---

### Post by southernman on 2007-09-06
Did you make a backup copy of your file, before seriously hacking it apart.... again?

During the reconfiguring process, had you chosen the "medium" option (I forget what step, but it's toward the end) you could have chosen what res you wanted to use.

IS your monitor capable of doing 1200x676 @ 60hz. Just cause it can do 1280x720@50 doesn't mean it will do as you are trying. If you have the manual check it, if not google it to be certain... if you've already done so or know this to be doable carry on McDuff! ;)

My level of experience from above will do you no good. Surely someone else will come along that can better guide you.

---

### Post by Sprogg2001 on 2007-09-06
will try again using the medium option

I know the monitor can support this res because windows does the same thing sets it up using 1280x720 and I then use the nvidia control panel to resize the desktop area whic then drops the res to 1200x676 

so will let you know how it turns out

---

### Post by Harpoon on 2007-09-06
I searched using you video caard + resolution, aand found this:
[http://ubuntuforums.org/showthread.php?t=538804&highlight=Nvidia+7600+resolution](http://ubuntuforums.org/showthread.php?t=538804&highlight=Nvidia+7600+resolution)

Take a look at the thread and see if the advice doesn't fit your situation.

---

