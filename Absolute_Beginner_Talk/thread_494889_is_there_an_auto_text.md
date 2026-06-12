---
title: "is there an auto text ?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-07-07
ok i used to use an apps named texter by lifehacker, i really miss it.. here is a description for people who don't know what i am talking about

"Text substitution app Texter saves you countless keystrokes by replacing abbreviations with commonly used phrases you define.

Unlike software-specific text replacement features, Texter runs in the Windows system tray and works in any application you're typing in. Texter can also set return-to markers for your cursor and insert clipboard contents into your replacement text, in addition to more advanced keyboard macros. Did we mention it's free?"

IS THERE AN SOFTWARE LIKE THIS FOR LINUX ? THANKS

---

### Post by ukripper on 2007-07-07
Try Jedit - Here is link [http://www.jedit.org/index.php?page=download](http://www.jedit.org/index.php?page=download)

Did i mention it is also free?

---

### Post by AhJah on 2007-09-19
this thread is about a text replacement utility, not a text editor.

---

### Post by rob_65 on 2007-10-26
I'm also interested as to whether there's anything like this for linux - it seems like a good idea.

Anyone know?

---

### Post by 3rdalbum on 2007-10-26
I'm shr it wrks well til u use sum1 else's cmptr... ;-)

---

### Post by peabody on 2008-02-18
I realize this is an old thread, but my text replacement program autokey has become somewhat usable.  The link to my project's sourceforge page is in my signature.  If you're feeling brave enough, please give my program a chance and let me know if it works for you.

---

### Post by HunkieChan on 2008-02-18
hey bro, thanks.. i will give it a try !

---

### Post by kristian.rekovic@gmail.co on 2008-02-22
hey guys do you need any help with the autohotkey conversion, i do a lot of macro programming in autohotkey, and i really need autotext feature it would be nice i work and live by autohotkey ahk files lol. so this would be a nice implementation i have been looking around for 4 months with no results so for of any type of autotext exept for kde and im not a fan no insult to anyone lol, i like my gnome.

---

### Post by peabody on 2008-02-22
[http://ubuntuforums.org/showthread.php?t=703736](http://ubuntuforums.org/showthread.php?t=703736)

[http://autokey.sf.net/](http://autokey.sf.net/)

Yes I need quite a bit of help.  I actually can't work on my project until summer because I'm swamped with school currently.

Currently, my autokey program only implements the hotstring feature of autohotkey, and not all that well at that.  I would be interested in implementing autohotkey's language, but that would be a huge undertaking.  It would require writing a parser and making equivalents for all functions in Autohotkey's language.

While AHK is open source, it is too windows specific to convert.  It is quite literally easier to start from scratch.

Rome wasn't built in a day, I expect the undertaking to take years.

---

### Post by kristian.rekovic@gmail.co on 2008-06-24
Here is a present for you :) pyatspi it's like api for windows, i put the little code below together, forget the keylogger, atspi has everething you need, as well as more. but here is a usefull example for you below. contact me via email [email]kristian.rekovic@gmail.com[/email]

#/usr/binenv python
#gexpansion.py
#
# requires pyatspi in > synaptic
# eather manually enable atspi keyboard accesability
# or install acerciser in > Applications-add programs-Programming (make sure u enable all repos for this install)
# Run acerciser and it will ask if you want to enable keyboard accesability say yes, log out of gnome and log back in then bang the #script below will work just don't forget to install pyatspi.
#
#Program information: Gnome text expansion utility.
#             Author: Kristian Rekovic
# gexpansion - gnome text expansion utility written by Kristian Rekovic.    
# Copyright (C) 2008  Kristian Rekovic
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

import pyatspi 
import os         
import string
import sys
import re

def callback(event):

 os.system(['clear'][os.name  == 'linux'])  #Clear linux console
 string_event = str(event)                  #Convert event to string 
 keystring = string_event[37]               #Prints the letter of the string pressed
 hwcode = string_event[19]+string_event[20] #hwcode:Hardware code for pressed key <--- i prefer this when dealing with st
 print keystring #<----------- keystring of released key
 print hwcode    #<----------- Hardware code for pressed key.
 print event     #<----------- Raw data i converted to text in event_string then parsed in keystring and hwcode. 
                 #If you look up pyatspi in google you will se more example code which has a full accesability feature
                 #It's kind of like api for windows but a hell of a lot better. :) Enjoy.

reg = pyatspi.Registry
reg.registerKeystrokeListener(callback, mask=pyatspi.allModifiers())
reg.start()

---

### Post by kristian.rekovic@gmail.co on 2008-06-24
[http://gexpansion.sourceforge.net/](http://gexpansion.sourceforge.net/)
Linux autotext written by me check it out.

---

### Post by kristian.rekovic@gmail.co on 2008-07-11
[http://gexpansion.sourceforge.net/](http://gexpansion.sourceforge.net/)
Linux autotext written by me check it out.

---

### Post by kristian.rekovic@gmail.co on 2008-07-24
> **kristian.rekovic@gmail.co said:**
> hey guys do you need any help with the autohotkey conversion, i do a lot of macro programming in autohotkey, and i really need autotext feature it would be nice i work and live by autohotkey ahk files lol. so this would be a nice implementation i have been looking around for 4 months with no results so for of any type of autotext exept for kde and im not a fan no insult to anyone lol, i like my gnome.

ok guys im done with the first part of my program fully working autotext with the option of running commands and so forth with the help of xautomation go to htto://gexpansion.sourceforge.net , i will be makeing this a deb file install soon, but we all know makeing deb files is a pain in the rear.

---

