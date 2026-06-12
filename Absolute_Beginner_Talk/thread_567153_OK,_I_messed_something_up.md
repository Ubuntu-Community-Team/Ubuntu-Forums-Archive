---
title: "OK, I messed something up"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by BOZG on 2007-10-04
I installed both the DivX 6.1.1 codec and the Ubuntu restricted extras package [see here](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29) to see if I could get a better divx player than totem but now I can't actually read anything.  All characters in the bars and and menus are blocks.  What do I do?  I can't even find the restricted extras package cause I can't read anything and I'm not sure how to remove divx codec.

---

### Post by BOZG on 2007-10-04
OK, I''ve managed to remove restricted extras and nothing has happened so it appears to be the divx codecs.

---

### Post by BOZG on 2007-10-04
[IMG]http://img.photobucket.com/albums/v338/BOZG1/Screenshot.png[/IMG]

This is what my title bars and menus are currently like.

---

### Post by BOZG on 2007-10-04
Tried changing fonts in the font menu but they all appear as blocks.

---

### Post by Paul820 on 2007-10-04
See if this will help you [http://ubuntuforums.org/showthread.php?p=3469380]("http://ubuntuforums.org/showthread.php?p=3469380")

---

### Post by BOZG on 2007-10-04
No, still not working after reboot.

---

### Post by Paul820 on 2007-10-04
What about your default language, has something changed it? Check language support.

---

### Post by BOZG on 2007-10-04
Can you guide me to it?  I can't actually read anything in the menu so I can't actually see where I'm going?  Thanks.

---

### Post by Paul820 on 2007-10-04
Go to Sytem->Preferences->Main Menu, in the left box click on Preferences again, in the right box look for 'Control Centre', check the box. Now go back to system->Preferences again and click on 'Control Centre', language support is in there under system. Check if your language has been changed from there.

---

### Post by BOZG on 2007-10-04
I mean that I can't find the main menu because I can't read the titles.  What are you the icons or possibly can you count down the number of titles so I know which one is which?  Sorry about this.

---

### Post by multifaceted on 2007-10-04
This happened to me when I booted the LiveCD over an install to modify the partitions. It did it only once though.... maybe this is irrelevant but, who knows... it be some sort of a clue?

---

### Post by BOZG on 2007-10-04
I've rebooted a few times and still no change.  If I run Ubuntu through the LiveCD, it's fine.

---

### Post by Paul820 on 2007-10-04
Ok, sorry about that :) open the terminal and type gnome-control-center, look for the flag, click there. There is a small downward pointing arrow, select your language from there if you can read it.

---

### Post by BOZG on 2007-10-04
[IMG]http://img.photobucket.com/albums/v338/BOZG1/Screenshot-1.png[/IMG]

This is currently where I am.  I'm looking EN-GB or EN-IE.  Either will do. :)  The 27th box is checked on the list but I don't know what it is.

---

### Post by Paul820 on 2007-10-04
Wow, what a mess, the 27th box is english. Where them two little arrows are pointing up and down there are some more options, try and find yours from this shot

---

### Post by FuturePilot on 2007-10-04
Try
```
sudo dpkg-reconfigure fontconfig-config
```

---

### Post by Paul820 on 2007-10-04
> **FuturePilot said:**
> Try
```
sudo dpkg-reconfigure fontconfig-config
```
I just hope he can read the terminal properly, :)

---

### Post by BOZG on 2007-10-04
No, still nothing working.  I tried a few different languages to see if they'd work but nothing at all.

---

### Post by BOZG on 2007-10-04
Looks like I'll just have to reinstall everything.  Is there any repair option when installing Ubuntu or do you have to do a full install?

---

### Post by FuturePilot on 2007-10-04
Ok, one last shot here
```
sudo fc-cache -f
```
I'm sure there's a solution to this.

---

### Post by BOZG on 2007-10-04
Still doesn't work.  :)


I just hope that my graphics card drivers work this time.  Took ages to get them to work last time and I can't remember exactly what I did.

---

### Post by BOZG on 2007-10-04
How would I remove the DivX codec pack?  Might as well see if it has any effect or not.

---

### Post by BOZG on 2007-10-04
It appears that I'm back in business after a fresh install.

---

