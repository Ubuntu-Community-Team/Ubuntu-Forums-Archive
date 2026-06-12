---
title: "Desktop Themes."
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by nee coa la on 2006-01-18
Well I have been looking at many screenshots of other people's desktops and in a lot of them I see some icons for the proccesor and the weather. Now I made a new panel and added those but i can never seem to get the same effect? Anyone have any suggestions?

Also a lot of people have the MAC OS feel and the panel is not extended yet they do not have the little bars at the end of the panel? How would I get rid of them?

---

### Post by 23meg on 2006-01-18
You're looking for desklets.

[http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)
[http://adesklets.sourceforge.net/](http://adesklets.sourceforge.net/)

```
sudo apt-get install gdesklets adesklets
```

---

### Post by mustang on 2006-01-18
[QUOTE=nee coa la]Well I have been looking at many screenshots of other people's desktops and in a lot of them I see some icons for the proccesor and the weather. Now I made a new panel and added those but i can never seem to get the same effect? Anyone have any suggestions?
[/QUOTE]

Try ```
sudo apt-get install gdeslets
``` and head over to [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/) for various displays/sensors. aDesklets is also another widget program but it a bit more complicated to install. You also might want to give the immensly popular conky a shot ```
sudo apt-get install conky
``` Screenshots for conky [here.]("http://conky.sourceforge.net/")

> Also a lot of people have the MAC OS feel and the panel is not extended yet they do not have the little bars at the end of the panel? How would I get rid of them?

See my post here:
[http://www.ubuntuforums.org/showpost.php?p=559285&postcount=2](http://www.ubuntuforums.org/showpost.php?p=559285&postcount=2)

edit: doh! 23meg beat me to the punch

---

### Post by nee coa la on 2006-01-18
Well is there any other way to install those? I o not have root and so installnig them is rather difficult. I downloaded gDesklets from thier site and did what i think was installing it...i got this:

"Install_StarterBar_Sensor.bin" is an executable text file.
 and from there i click "Run In Terminal"

once i did that i got this message:

"The sensor has been installed successfully.
gDesklets is now able to use it."

Where do I go from there? I can't find it anywhere.

(sorry im asking such dumb questions but I have only been using Linux for about 3 days.)

---

### Post by 23meg on 2006-01-18
What do you mean you "don't have root"? Are you getting errors when you try installing them with "sudo apt-get install"? If so what errors?

---

### Post by Perfect Storm on 2006-01-18
What do you mean you don't have root? Are you a user on someone elses compter? The best then are to ask the person to install gedseklets.

---

### Post by nee coa la on 2006-01-18
Well my dad has been using linux for years now and I have been using windows. He doesn't want to give me root on my computer until I know more about the operating system so I don't **** thigns up. He is out of town though so im kinda stuck here without root for a few days...

---

### Post by Perfect Storm on 2006-01-18
Perhaps he alsready installed gdesklets. Try run **gdesklets** in the terminal.

---

### Post by nee coa la on 2006-01-18
Nope he didn't. Is that the only to install it? Is there any way to get it without root?

---

### Post by dueY on 2006-01-18
[QUOTE=nee coa la]Nope he didn't. Is that the only to install it? Is there any way to get it without root?[/QUOTE]

You should ask him for your own install on another partition or something because you will never learn Linux without having root :(

---

### Post by chadwick359 on 2006-01-18
> You should ask him for your own install on another partition or something because you will never learn Linux without having root

Yeah, I'm acutally suprised that anybody wanting their son to learn would allow them access, otherwise it's a fairly similar expereince to using Windows. Gogo terminal.

---

### Post by nee coa la on 2006-01-18
No no, it's not that I won't get root eventually its just that he wants to go over some stuff with me first and teach me how to ues linux first.

---

