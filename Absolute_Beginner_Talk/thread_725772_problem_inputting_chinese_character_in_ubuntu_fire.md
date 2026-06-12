---
title: "problem inputting chinese character in ubuntu firefox"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by takeuaway on 2008-03-16
hi, i have installed chinese support and SCIM, and i am fine with entering chinese characters in gedit and any openoffice.org, but i can't seem to enter chinese characters in the searchbox in mozilla firefox. 

Please help me, thanks

---

### Post by Slipmyknot101 on 2008-03-16
Is the search box the only place within Firefox in which you are unable to input Chinese characters? Or are you completely unable to input Chinese characters of any type in Firefox? Or is it something other than that?

Glad to assist,
Trevor

---

### Post by takeuaway on 2008-03-16
within firefox all cannot. Actually i just tried, i cant type chinese in openoffice.org also. But i can do so in gedit by right clicking and select SCIM input. 

Thanks for the help! :)

---

### Post by seshomaru samma on 2008-03-16
you are probably using an english session

you need to install scim-bridge
```
sudo apt-get install scim-bridge
```
then configure ubuntu to use it by editing the scim file
```
sudo gedit /etc/X11/xinit/xinput.d/scim
```

change the line:
```
GTK_IM_MODULE=xim
```
into :
```
GTK_IM_MODULE="scim-bridge"
```
and restart the computer
you should be able to start SCIM with ctrl+space
if it doesn't then you will need to use the im-switch 
let me know how it goes

---

### Post by takeuaway on 2008-03-20
thanks a lot! it helps! :)

---

### Post by mrund on 2008-04-07
I'm running an English session under Gutsy. I installed SCIM and SCIM-bridge as described here:

[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

Now Chinese characters work fine in gedit: I can switch between the English and Chinese input modes with CTRL-space. But this works neither in OpenOffice nor Firefox. OO thinks I want to enter a hard space, and Firefox doesn't react at all.

Any ideas how I can get SCIM to work in OO and Firefox? Or should I just instruct my Chinese wife to compose in gedit and paste her stuff into OO?

Maybe I could try to teach SCIM to use some really weird key combination as its toggle. Hmm...

---

### Post by seshomaru samma on 2008-04-08
did you edit the  xinput.d/scim file? (step number two in the link you provided)
it's a very important step, juts installing scim-bridge is not enough.

if you did and after reboot still can't use SCIM in OO and Firefox then use the im-switch
look at the link where it says "Under Ubuntu versions prior to Ubuntu 7.10" and follow their instructions

---

