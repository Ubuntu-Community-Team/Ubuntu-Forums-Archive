---
title: "update/download errors"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by hillbillybrit on 2007-10-23
Greetings all. So new to here I've still got the label attached.
Ubuntu installed in about an hour on this old p3 and I was quite happy to plod my way through updates etc. Internet worked eventually after reconfiging the router but then all my woes began.
Re- finding all my old web sites was easy enough til i got to youtube.
I need to install java but it fails over and over wether from the add/remove list or if i try it from the youtube site.Much as I love to play with new toys and ubuntu is just that, I'm getting a bit sick of these constant update and download fails. I'm guessing that there is a fundamental fault in my original setup that is not allowing these installs.
Until i can get the java working i guess i'm stumped.
so glad you made this forum though. I've seen some really useful advice and tons of other issues and hope this one can be solved as easily.
heres one i get a lot of
E: tzdata: subprocess post-installation script returned error exit status 10

---

### Post by kcy29581 on 2007-10-23
Not at a Ubuntu machine right now, but I'll try to help.

[LIST]
[*]Navigate (from the menus in the top-left corner) to: System -> Administration -> Synaptic Package Manager
[*]Click on "Search" and search for "sun-java6-plugin" and install it (tick the checkbox and then click on apply)
[*]When everything finishes installing, open up firefox and try a Java site.[/LIST]Good luck

---

### Post by hillbillybrit on 2007-10-23
Thanks for the rapid reply.
Tried it and got the same eror message
E: tzdata: subprocess post-installation script returned error exit status 10
I'm guessing its a more fundamental corrupt file somewhere not allowing any installs

__________________

---

### Post by trak87 on 2007-10-23
Problems began at youtube? That site requires the flash plugin ("flash-nonfree"). I don't think it requires Java.

---

### Post by hillbillybrit on 2007-10-23
its the eame error message on the youtube download or off the ubuntu software
apparently yup i do need java too for more than you tube and get that same fault as for the flash download

---

### Post by kcy29581 on 2007-10-23
Did you click the "Reload" button first? Perhaps it needs to refresh your download sources.

I'll think some more on this.

---

### Post by kcy29581 on 2007-10-23
You may have hit this bug: [https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/116193](https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/116193)

What timezone are you in?

---

### Post by hillbillybrit on 2007-10-23
I'm on eastern time as in west virginia
yup i think its a bug as it is affecting other unrelated downloads and installs

---

### Post by kcy29581 on 2007-10-23
Could you try changing the timezone to Europe/Berlin as the bug report suggested? Right-click on the time on your desktop (top-right corner) and find the preferences to change the timezone.

Then re-enter Synaptic, reload and retry the java download.

---

### Post by hillbillybrit on 2007-10-23
I am on bended knee to your sagelike wisdom thankyou. 
I'm not one to read a manual or instructions so I just went straight into the time zone and changed it to sunnier climes and it worked in an instant. now its working I don't know wether to go in and change it again to the recommended Berlin.I was still reading your reply as i did the changes and never got to the link lol
Now I gotta get out of that stupid windows habit of rebooting every time I make a dramatic change to something.

               Note to the wise. Kentucky is one of the bug zones

---

### Post by kcy29581 on 2007-10-23
> **hillbillybrit said:**
> I am on bended knee to your sagelike wisdom thankyou. 
I'm not one to read a manual or instructions so I just went straight into the time zone and changed it to sunnier climes and it worked in an instant. now its working I don't know wether to go in and change it again to the recommended Berlin.I was still reading your reply as i did the changes and never got to the link lol
Now I gotta get out of that stupid windows habit of rebooting every time I make a dramatic change to something.

               Note to the wise. Kentucky is one of the bug zones
Glad I could help in time! I'm getting on a plane for the next 10-12 hours in a bit!

I know they are/have (not sure) releasing a fix; hopefully this will be the last of it.

Enjoy Ubuntu my friend!

---

### Post by leexgx on 2007-10-23
you talked about no internet before you started norm do the below as it mite be the problem

[https://bugs.launchpad.net/ubuntu/+s...ty/+bug/154095](https://bugs.launchpad.net/ubuntu/+s...ty/+bug/154095) do the below

goto System > Admin > software sources

1 Tick all boxs apart form source code (do not think norm users need that)
2 Pick your Download From server location (as it picks main server by default click on search if you cant see one for you)
3 Goto updates and tick the first 2 options (top ones, other 2 is Up to you but should read up first)
4 [recommended but Optional] change the auto up date check to [Download all updates in background] (assuming you do not have an hard disk that is very small its an better option so your ready to install when you are ready just means you do not need to have to wait for them to download)

I do not recommend auto install with out confirmation Option as it may not wait for all updates to be install when shuting down the pc, as it make brake your box

---

