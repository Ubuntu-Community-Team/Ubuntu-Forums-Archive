---
title: "Installing drivers and failing"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Haruko147 on 2007-06-15
Let me foward this by saying I'm 100% new and all I know about linux has been learned in the past 3 hours

Ok, so I have a broadcom 43xx wireless

Apparently the one of two options to get it running are to download some application called bcm43xx-fwcutter and use it to place some sys file called bcmwl5.sys wherever it happens to go. 

[http://ubuntuforums.org/showthread.php?t=185650](http://ubuntuforums.org/showthread.php?t=185650)

I first installed and unzip the file on my windows xp comp and moved it over on the desktop of my linux comp.
  
then I've used sudo apt-get install bcm43xx-fwcutter, but it does about 3 lines of preparation finally saying impossible to find packet bcm43xx-fwcutter. I can't find anything named that to install with the add/remove applications or synaptic. Do I have to put the files somewhere special to be reconized? I really have no idea.

The second option is to use something called ndiswrapper, but that the extent I know about it.

[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper+54+mbps](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper+54+mbps)

I've followed up to step 5 where it wants to install build-essential. Of course it can't find such a file, I don't know whether it needs to be downloaded. Later on the guide even tells me to get a file from the internet, but I can't because that precisely the problem I'm trying to fix. If I dl it on my windows computer and move it over I'm not sure what the commands are telling me to do and where I should put the file to make them owrk properly.

Anyone help a poor noob?

---

### Post by bluvy on 2007-06-16
I'm a complete noob, and I have broadcom too
this thread [http://ubuntuforums.org/showthread.php?t=405990&highlight=easy+broadcom+wireless]("http://ubuntuforums.org/showthread.php?t=405990&highlight=easy+broadcom+wireless")
really helped me out! works like magic

---

### Post by Haruko147 on 2007-06-16
hmm, I'll check it out *crosses finger* ^^

---

### Post by Haruko147 on 2007-06-16
Ok, so I ran that file. The only visable difference I can see is now the option for wireless is deleted out of my manual configuration, and my internet still doesn't work. 7 hours working on this problem lol, I don't know what to do now :(

---

### Post by Haruko147 on 2007-06-16
Whoops, had to do a little more tweaking but it turned on ^^ I love you all who wrote the scripts and directed me to them! I love ubuntu!

---

