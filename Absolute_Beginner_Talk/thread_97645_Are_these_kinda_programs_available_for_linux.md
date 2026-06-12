---
title: "Are these kinda programs available for linux?"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by dronepower on 2005-12-01
I just started trying out linux with puppy linux on my secondairy machine. All went fine. Now Im thinking of trying Ubuntu on my main machine.

My question is if there is a reasonable linux alternative for adobe illustrator / coreldraw, and video editing programs like pinnacle / adobe premiere.

I above answers are positive Im a happy man :) 

cheers,

---

### Post by Brunellus on 2005-12-01
For adobe illustrator, look for inkscape, which is a vector drawing program.  Pretty damn cool.

---

### Post by arpunk on 2005-12-01
[QUOTE=dronepower]I just started trying out linux with puppy linux on my secondairy machine. All went fine. Now Im thinking of trying Ubuntu on my main machine.

My question is if there is a reasonable linux alternative for adobe illustrator / coreldraw, and video editing programs like pinnacle / adobe premiere.

I above answers are positive Im a happy man :) 

cheers,[/QUOTE]
For pinnacle you can try out kino, it does the job but isnt advanced as pinnacle.
```
Description: Non-linear editor for Digital Video data
 Kino allows you to record, create, edit, and play movies recorded with DV
 camcorders. Unlike other editors, this program uses many keyboard commands
 for fast navigating and editing inside the movie.
```

---

### Post by Freddie.Ruddick on 2005-12-01
Pretty much the only video editor for ubuntu is Kino.

EDIT: Damm! That was fast typing arpunk!

---

### Post by arpunk on 2005-12-01
[QUOTE=Freddie.Ruddick]Pretty much the only video editor for ubuntu is Kino.

EDIT: Damm! That was fast typing arpunk![/QUOTE]
hehe ;) :P

---

### Post by dronepower on 2005-12-01
Well if Kino is capable of roughly editing my home video, cutting out bad pieces, and save the file in mpeg4 format Im happy.

1st I got to solve my brown screen + mouse cursor problem I get after my install :(

---

### Post by Brunellus on 2005-12-01
well then tell us what that problem is and we'll solve it.

Note that you will probably want the RestrictedFormats wikipage in the near future, re your video rendering

---

### Post by 23meg on 2005-12-01
[QUOTE=dronepower]
1st I got to solve my brown screen + mouse cursor problem I get after my install :([/QUOTE]
If you have nvidia hardware it's a known problem; install the proprietary nvidia driver or switch to the vesa driver to get rid of it.

For video editing also check out Cinelerra which is more advanced than Kino.

---

### Post by dronepower on 2005-12-01
[QUOTE=23meg]If you have nvidia hardware it's a known problem; install the proprietary nvidia driver or switch to the vesa driver to get rid of it.

For video editing also check out Cinelerra which is more advanced than Kino.[/QUOTE]


The proprietary nvidia driver means? 
I get faster help with this problem while being kinda offtopic than in my other topic in the install / upgrade forum :cool: 

I check those programs.. yes, I will be video encoding from DV AVI format to MPEG4 format, so I can burn it on DVD.

I use a neo2 nforce3 board with a Gforce 6800LE card

---

### Post by dronepower on 2005-12-01
I found this

[how to load vesa drivers etc.]("http://www.ubuntuforums.org/showthread.php?t=94992&highlight=proprietary+nvidia")

took some searching :cool:

---

### Post by 23meg on 2005-12-01
[Here]("http://www.ubuntuforums.org/showthread.php?t=75074") is how to install the proprietary driver. If you want a free driver you can use vesa by putting "vesa" instead of "nv" in the Device section of your xorg.conf file. Vesa is slower compared to the nvidia driver.

---

### Post by dronepower on 2005-12-01
ya I found that link, well, in VESA it runs well. I installed the nvidia driver, rebooted, but I cant see the nvidia setting, and I cant change resolution greater than 1023x768, but I will figure it out

---

### Post by reuben on 2005-12-09
Try Main Actor for video editing. It is tons more stable than Cinelerra. It's commercial software tho. (There's a free preview download)

[http://www.mainconcept.com/mainactor_info.html](http://www.mainconcept.com/mainactor_info.html)

---

### Post by prizrak on 2005-12-10
[QUOTE=dronepower]ya I found that link, well, in VESA it runs well. I installed the nvidia driver, rebooted, but I cant see the nvidia setting, and I cant change resolution greater than 1023x768, but I will figure it out[/QUOTE]
Try ```
apt-get install nvidia-settings
```
They get put into Applications>System Tools>NVIDIA Settings
Alternatively go to your terminal and type ```
nvidia-settings
```
Also for resolution you might want to edit the Xorg.conf file (dat is what I hear round the forums at least)

---

### Post by Gustav on 2005-12-10
For resolution, look at this [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by kperkins on 2005-12-10
I like avidemux for the little video editing that I do. Inkscape is an excellent vector editor.

---

### Post by davebgimp on 2005-12-10
[QUOTE=Brunellus]For adobe illustrator, look for inkscape, which is a vector drawing program.  Pretty damn cool.[/QUOTE]

As a user of Adobe Illustrator at work and Inkscape at home, I find myself really frustrated with it. Just basic things I take for granted or things I **need** to do are pointless in Inkscape or unnecessarily obfuscated. I'm tempted to install Illustrator through Wine, just so I can maintain some sanity when I try to make something. 

I just feel like Inkscape has a really long way to go, much more than Gimp in terms of supplying free alternatives to Adobe products (though Gimps lack of support for CMYK is pretty rough). Gimp was a joy to switch to, so much so that it's shortcomings are easy to forgive. It's just not the case with Inkscape, unfortunately.

I'll keep checking out Inkscape, but so far it's just not doing the job. I'm still hopeful, though.

---

