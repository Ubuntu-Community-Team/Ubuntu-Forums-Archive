---
title: "[SOLVED] Clear find files history"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by kuric on 2007-07-17
Hi everybody,

I would like to know how to clear "find files" history on Ubuntu 7.04.

Thank you.

---

### Post by Super TWiT on 2007-07-17
You can clear it by going into the Places menu and mousing over Recent Documents and clicking on the Clear Recent Documents button.

---

### Post by kuric on 2007-07-17
Thank you but that didn't work. 

My previous searches on "find files" still appears on the combo box.

Anyone else has another sugestion?

---

### Post by Super TWiT on 2007-07-17
Oh, I thought you meant your documents history.  I guess I should have paid more attention to the thread title.  :)  My previous searches don't show up on my computer.

---

### Post by kuric on 2007-07-17
Dont worry :)

For example, I know how to clear it on Kubuntu / Kfind. 

We have to edit /home/%user%/.kde/share/config/kfindrc and go to Patterns=

But I can't find any similar file on Ubuntu... :(

---

### Post by naem657 on 2007-07-25
I found it...   :D

After looking for much in Internet (without answers apparently) i decided on a little ingenious solution. 

with the finder looks for a file that contained some of the words that were in the history  and marks to look for hidden files.

well the file that needs edit is:

home/(your user here)/.gconf/apps/gnome-settings/gnome-search-tool/%gconf.xml

before:
> 
<?xml version="1.0"?>
<gconf>
                <entry name="history-gsearchtool-file-entry" mtime="1185410708" type="list" ltype="string">
                <li type="string">
                        <stringvalue>[COLOR="Red"]any word for example[/COLOR]</stringvalue>
                </li>
        </entry>
</gconf>


after: 
> 
<?xml version="1.0"?>
<gconf>
</gconf>


thats all

pd. sorry for my bad english, im mexican and i used google translator for this

---

### Post by kuric on 2007-07-28
THANK YOU naem657, it works :) 

Still, I had to restart X, because gnome-search-tool was showing my previous searches, even after editing that file... LOL.

Good work, thanks a lot!

---

### Post by John Macnab on 2007-07-29
Great!I was looking for this too :)

---

