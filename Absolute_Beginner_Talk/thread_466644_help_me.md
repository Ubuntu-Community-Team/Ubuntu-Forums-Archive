---
title: "help me"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by reston5 on 2007-06-06
i just got a view sonic monitor that is 1440x990 natively what do i do i dont no how to change it 

its ecs on board video and i am a complete noob when it comes to editing the etc files

---

### Post by CaptainInsaneO on 2007-06-06
I don't quite understand what you're requesting help about...

Are you trying to lower or raise the resolution? If so, just click System>Preferences>Screen Resolution and go from there.

---

### Post by Hobo Joe on 2007-06-06
System>Preferences>Resolution. If it's not there, you may have to edit a file, but it should be on the list.

also, what is your video card? Drivers are something you might want.

Only under extreme circumstances should you manually change any of the configuration files.

---

### Post by Ek0nomik on 2007-06-06
I presume that those options aren't there?

If not, you can edit your xorg.conf file by following this:

First, backup your xorg file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Now you can edit the file:

```
gksudo gedit /etc/X11/xorg.conf
```

Example:

	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection

and you can add 1440x990 to your list in each section.  Just make sure that 1440x990 is the correct resolution that your monitor supports.

If that doesn't work, respond and we can try a few more things.

---

### Post by Hobo Joe on 2007-06-06
> **Ek0nomik said:**
> I presume that those options aren't there?

If not, you can edit your xorg.conf file by following this:

First, backup your xorg file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Now you can edit the file:

```
gksudo gedit /etc/X11/xorg.conf
```

Example:

	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection

and you can add 1440x990 to your list in each section.  Just make sure that 1440x990 is the correct resolution that your monitor supports.

If that doesn't work, respond and we can try a few more things.

While this is good advice, I don't think he even knew about the screen resolution option under preferences, and it may just be me, but it doesn't really sound like he's ready to be running stuff like this just yet. :)

But it is good incase the resolution isn't there.

---

### Post by reston5 on 2007-06-06
hey hobo joe 

its an intel onboard the drivers that came with the ecs board didint work

im trying to raise the resolution to 1440*990

what can i do without editing the etc file

---

### Post by Hobo Joe on 2007-06-06
> **reston5 said:**
> hey hobo joe 

its an intel onboard the drivers that came with the ecs board didint work

im trying to raise the resolution to 1440*990

what can i do without editing the etc file

Did you check the menu location that I gave you? That will give you a little menu with a few options for resolutions. If 1440x900 isn't on the list, I'd try what Ek0nomik suggested.

---

### Post by CaptainInsaneO on 2007-06-06
You might also need to check whether your onboard supports a resolution that high. I have onboard Intel and mine only goes up to 1024x768, no matter what monitor I'm using.

---

### Post by punx45 on 2007-06-07
yeah, knowing the exact chipset will be helpful.   go to the console and run 
```
lspci 
```
then cut and paste the output here.

---

### Post by reston5 on 2007-06-07
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

thats the copy of it will it not support higher than 1024x768

---

### Post by CaptainInsaneO on 2007-06-07
The highest supported res. on that is 2048x1536.

Do what Hobo Joe said, that's the best advice I have for you at this point. (It's 10 at night and I'm tired. :p)

---

