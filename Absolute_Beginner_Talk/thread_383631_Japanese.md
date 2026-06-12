---
title: "Japanese"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by violagirl on 2007-03-13
I am very frustrated because I am rather new to Linux and cannot figure out how to get Japanese working properly.  I tried looking on several website to no avail.  I tried this website: [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM) but if I look at one of the first steps, where you go to language support and check the languages you want to install, the only one listed there is English on mine, verses the one in the picture that has TONS listed!!  That's why I'm so confused.:mad: :mad:To make it worse, I have no internet connection on that computer, so I have to install things networklessly.  I was thinking maybe there was some way I could take it from SCIM or something off the CD, but I haven't figured out how to do that the right way.  I'm sorry I'm so stupid, but could anyone explain to me how to do this?

---

### Post by shirilover on 2007-03-13
You may need to add Japanese language support.

```
sudo aptitude install language-pack-ja language-pack-gnome-ja
```

substitue language-pack-kde-ja if you're using KDE instead of Gnome.

I happened to have used the guide located here [http://www.mrbass.org/linux/ubuntu/scim](http://www.mrbass.org/linux/ubuntu/scim/)

---

### Post by Najand on 2007-03-13
First of  all, you need to turn down the apt internet updates. Use "Software Sources" located in:
System => Administration
And uncheck all boxes under internet.
Then, close it and insert your ubuntu cd-rom.
You will be prompted that "Ubuntu CD-ROM" has been found. Follow dircetions to add it.
Then open "Synaptic Package manager" located in System => Administration
And click on "Reload".
If everything was fine, then go to "System => Administration=> Langauge Support" and check "japanese" there. You will be asked if you want to install new packages or not and afterwards, it will install neccessory packages for you.
After everything is done and nothing goes wrong, you would probably be able to use "Shift+Space" to toggle between Japanese and English.

---

### Post by violagirl on 2007-03-13
I tried the command in the first user's post with the CD in and it didn't find anything.  I didn't see the tab "Software Sources" but I did see one with "Software" in it.  Is this because I am using Dapper?  I tried unchecking the boxes about getting updates from the internet but saw nothing else on that manner.  When I go into the Synaptic and press reload, however, it still tries to grab from the internet (and CD) and fails for the internet part at least, but if I look under the software list under langauge support, japanese still isn't listed.  GRAH! 
 &#12420;&#12420;&#12371;&#12375;&#12356;&#12424;!!!!!&#12290;&#12539;&#12444;&#12539;(&#12494;&#1044;`)&#12539;&#12444;&#12539;&#12290;

---

### Post by Najand on 2007-03-13
&#33258;&#27578;&#12375;&#12394;&#12356;&#12391;&#12367;&#12384;&#12373;&#12356;&#12397;&#12290;(&#31505;)
If you have internet somewhere else, just download the packages and then take it using a stick memory or something, then use  "sudo dpkg -i <PACKAGES>" (must change <PACKAGES> with your package names) to install them. 
Try to download the following packages from: packages.ubuntu.com
*uim 
*anthy 
*scim-gtk2-immodule 
*scim-uim
*scim-tables-ja
*ipafonts
Then restart your xorg using Ctrl+Alt+BackSpace
If you couldn't do  that, I can help you installing them using Dapper CD in the terminal.

---

