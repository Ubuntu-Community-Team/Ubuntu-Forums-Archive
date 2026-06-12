---
title: "virtualbox questions about install"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by broekskw on 2008-02-13
ok have win xp on a computer that i would like to install virtualbox and then get ubuntu install then see if works all ok before doing another computer the other way, ubuntu virtualbox win xp

but on the first computer i downloaded the program and followed the guide (innotek virtualbox user guide)
on install i got this windows error "this software you are installing has not passed windows logo testing to verify its compatibility with windows xp"
continuing your installation of this software may impair or destabolize the correct operation of your ststem, either immediatley or in the future,microsoft strongly recommends that you stop this installation now and contact the software vendor for software that has passed windows logo testing

so i just click continue anyway and it then installs, so after that i go threw the setup guide and complete the setup and then open virtualbox and then start program but get another error message

"fatal no bootable medium found? system halted, this comes on the window that should load up virtual box

is this because i only have one os system installed windows xp??

please help  thanks:lolflag:

---

### Post by overdrank on 2008-02-13
> **broekskw said:**
> ok have win xp on a computer that i would like to install virtualbox and then get ubuntu install then see if works all ok before doing another computer the other way, ubuntu virtualbox win xp

but on the first computer i downloaded the program and followed the guide (innotek virtualbox user guide)
on install i got this windows error "this software you are installing has not passed windows logo testing to verify its compatibility with windows xp"
continuing your installation of this software may impair or destabolize the correct operation of your ststem, either immediatley or in the future,microsoft strongly recommends that you stop this installation now and contact the software vendor for software that has passed windows logo testing

so i just click continue anyway and it then installs, so after that i go threw the setup guide and complete the setup and then open virtualbox and then start program but get another error message

"fatal no bootable medium found? system halted, this comes on the window that should load up virtual box

is this because i only have one os system installed windows xp??

please help  thanks:lolflag:

HI and on the virtual box window you will see a settings button and select it and there you can setup  you virtual machine. You will need to enable your cd drive and this may help.

---

### Post by raydeen on 2008-02-13
That just means that your virtual HD that you created isn't formatted and set up yet. Check your settings to make sure that VirtualBox has mounted the CD drive and that VirtualBox will look at the CD drive first before the virtual HD. You should be able to boot with your Ubuntu disc inside VB and then format and install to the virtual HD. 

When you start VB, click the virtual machine you created and then click the Settings button at the top. Once in there, make sure to mount your computers CD drive and also check the Boot Order (under the Advanced tab). Just like a regular machine, you'll want VB to look at the CD drive first, then the Hard Drive. Hope this helps.

Oops. Someone beat me too it. :)

---

### Post by broekskw on 2008-02-14
great and thanks for your replies, will check that out right away. :guitar:

---

### Post by broekskw on 2008-02-14
one more question

i have one computer in a bual boot win xp and ubuntu, can i just install virtualbox and then set it up to run xp and ubuntu without restarting the computer to go from one system to the other??

or do i have to install virtualbox first then reinstall win xp as the quest and use ubuntu as the host??

thanks:guitar:

---

### Post by raydeen on 2008-02-14
If I'm understanding you correctly, you could go either way with this. You could install VB in Windows and run Ubuntu from there or install VB in Ubuntu and run Windows from there. I've done both methods (plus a third where I have Windows and Ubuntu on a MacBook :)). The only thing you're really going to lose is 3D acceleration in the virtual environment. You won't get the Compiz Cube if you do virtual Ubuntu and you won't have all the neat games if you do virtual Windows. I'd consider which OS you're going to use the most and then virtualize the other(s).

---

