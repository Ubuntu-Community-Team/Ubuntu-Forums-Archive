---
title: "Changing grub"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-10-10
can i change the look of Grub? and how can i change the commands because instead of having Ubuntu and WinXP the Ubuntu commands are doubled! so any help!?

---

### Post by elettronicha on 2006-10-10
> **Mazen said:**
> can i change the look of Grub?
Search the forums 'grub splash', you'll find a lot of topics.

> and how can i change the commands because instead of having Ubuntu and WinXP the Ubuntu commands are doubled! so any help!?

Please, search the wiki before: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Bye!

---

### Post by thojoh on 2006-10-10
hi there,


I think I have the same question:

With every new ubuntu kernel version, the GRUB loader adds another option to my GRUB menu at start up, so instead of having two options (Ubuntu and WindowsXP) in my Boot menu, I have now so many Ubuntu kernel options that for WindowsXP I have to scroll down the page to be able to choose it.
For a while, that was OK, but by now, it is getting a bit complex, so I'd like to change my GRUB menu so that it only shows the most recent Ubuntu kernel + Windows as the two options.

How can I do that?

I checked the link of the Wiki that was recommended, but couldn't find the information I need (maybe if I was more versatile with Linux, but as it is I am a bit afraid of making a stupid change in a vital bit of my computer - so unless I am sure I know what I am doing I don't want to mess with the GRUB loader).

thanks for any directions!

thomas

---

### Post by petri on 2006-10-10
In terminal
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
```
gksudo gedit /boot/grub/menu.lst
```
Find lines > ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2

As you see I have a line > # howmany=2 and I get in the grub the two latest kernels with their recovery  alternatives and windows. Do not uncomment any line just change **all** to a number.

Save and close gedit. 

If you want to learn more about grub check out Hermans site: [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) 
more usefull information at aysius site: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)


EDIT: As elettronicha says below you have to do ```
sudo update-grub
``` in terminal to get a new menu.lst and you will see the effects at restart. Tip: do just one modification at a time ;)

---

### Post by elettronicha on 2006-10-10
Here there are some lines of my /boot/grub/menu.lst, as an example. You mustn't uncomment the lines with one '#' character, but just edit them, since the script 'update-grub' will recognize them when it's launched and will provide to build the menu.lst as it's written in those options.

> 
## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# [COLOR="Red"]alternative=false[/COLOR]
If I remember well, when it's false it will remove the lines with the alternative rescue mode kernel.



> ## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# [COLOR="red"]lockalternative=false[/COLOR]

> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# [COLOR="red"]defoptions=verbose splash[/COLOR]
The options added at the end of every kernel entry (see towards the bottom of your menu.lst). For example, I replaced 'quiet' with 'verbose' and every time I update or install a new kernel (that's to say every time update-grub script it's automatically called) those lines will appear in the new kernel entry.



> ## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# [COLOR="red"]lockold=false[/COLOR]
I don't remember. Shame on me! ;)



> ## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# [COLOR="red"]altoptions=(single-user mode) single[/COLOR]
The lines which are added to the alternative kernel options, in case it exist. In my case, I don't want an alternative kernel, as I wrote before.



> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# [COLOR="red"]howmany=1[/COLOR]
Here it is what you want! Here you can choose how many kernel entries you want to find in grub. I want to run only one kernel, the latest one. If you wanted 2 kernels, you should replace 1 with 2, the latest and the last but one kernel versions, etc.



> ## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# [COLOR="red"]memtest86=false[/COLOR]
When it's false the memtest entry is removed.



> ## should update-grub adjust the value of the default booted system
## can be true or false
# [COLOR="red"]updatedefaultentry=false[/COLOR]
I don't remember.


When all is set as you like, run 'sudo update-grub' and you will reconfigure you're grub menu.

Bye!

---

### Post by Tomosaur on 2006-10-10
You may want to take a look at the link in my sig :)

Hope you get what you're after.

---

### Post by thojoh on 2006-10-10
thanks for all the information, guys!

I am well provided for, now.   :p

thom

---

