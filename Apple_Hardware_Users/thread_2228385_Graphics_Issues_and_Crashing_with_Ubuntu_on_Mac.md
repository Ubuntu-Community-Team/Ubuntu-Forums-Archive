---
title: "Graphics Issues and Crashing with Ubuntu on Mac"
date: 2014-06-07
forum: Apple Hardware Users
---

### Post by lachiw98 on 2014-06-07
I am using ubuntu 14.04 LTS on a 2010 mac book. My graphics card is a Nvidia 320m. I use i3wm with LightDM.
Usually the graphics mess up (virtical lines, boxes etc..) but sometimes this does not happen. After a while the system will hang, sometimes I can still move the mouse. After this sometimes it goes to a black screen displaying: [INDENT]* Starting LightDM Display Manager
* Stopping Send an event to indicate plymouth is up
* Starting Mount network filesystems
* Stopping Mount network filesystems
^@^@[ 1691.884024] nouveau E[xorg[8562]] failed to idle channel 0xcccc0000 [xorg[8562]]
[ 1706 884055] nouveau E[xorg[0562]] failed to idle channel 0xcccc0000 [xorg[8562]]
[/INDENT]
[INDENT]The rest of the output was garbled.
[/INDENT]
Othertimes instead of this output the system will return to the login screen.
I managed to retrieve the following information through ssh after one of the above black screens.
xorg.0.log: [http://pastebin.com/niYfZsWX](http://pastebin.com/niYfZsWX)
lspci -nn: [http://pastebin.com/vwwvztcB](http://pastebin.com/vwwvztcB)
dmesg: [http://pastebin.com/0esi7uG9](http://pastebin.com/0esi7uG9)
I have the same problem if I use the try Ubuntu option from a live cd

---

### Post by bapoumba on 2014-06-07
*Thread moved to **Apple Users**.*

---

