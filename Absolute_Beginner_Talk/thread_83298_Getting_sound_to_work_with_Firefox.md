---
title: "Getting sound to work with Firefox"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by elder68 on 2005-10-28
Presently I am using Kubuntu 5.04 and use Firefox for surfing the web. My problem is that when there is a sound link on a website, and I click on it, nothing happens. Sometimes I like to listen to news broadcasts from overseas News websites,  but presently I am blocked from doing this. Any help would be appreciated.

Thank you.

---

### Post by Robgould on 2005-10-28
Does sound work in your other applications?

---

### Post by Robgould on 2005-10-28
Need a little more info to help you.  Not sure what the real problem is.  Does sound jsut not work from firefox, or does it not work on your computer at all?

---

### Post by elder68 on 2005-10-28
[QUOTE=Robgould]Need a little more info to help you.  Not sure what the real problem is.  Does sound jsut not work from firefox, or does it not work on your computer at all?[/QUOTE]

Thanks, feeling a bit dumb, the sound is not on anywhere. I will have to work that out. Thanks for the help.

---

### Post by Robgould on 2005-10-29
from a terminal run

sudo alsamixer

make sure nothing is muted.  If you scroll all the way to the right you will find the external amp setting.  If you don't find anything else obvious, try toggling this and see if it works.  

If you are not sure how to use the terminal, do it this way

right click on the volume icon on your desktop and select "open volume control" from the context menu.  Again make sure nothing obvious is muted.  Click on edit in the toolbar and select preferences.  From the menu that appears, put a check in external amplifier and then click close.  Now click on the switches tab and you will see a check box for externam amp.  Try switching this on and see what happens.  Let me know.

---

### Post by elder68 on 2005-10-29
[QUOTE=Robgould]from a terminal run

If you are not sure how to use the terminal, do it this way

right click on the volume icon on your desktop and select "open volume control" from the context menu.  Again make sure nothing obvious is muted.  Click on edit in the toolbar and select preferences.  From the menu that appears, put a check in external amplifier and then click close.  Now click on the switches tab and you will see a check box for externam amp.  Try switching this on and see what happens.  Let me know.[/QUOTE]

Kmix was the utility driving the "volume control" but working my way through it I found the "external speaker" switch and turned it on. After that I had sound from the Cdrom, I then logged on to a site where I knew there was sound and it worked again. So thank you very much for help with this problem. :)

---

