---
title: "How do I install Mac OS X on Virtualbox"
date: 2010-06-27
forum: Apple Hardware Users
---

### Post by danielwtn on 2010-06-27
I am currently using Ubuntu 10.04 and Virtualbox on my computer, and I recently was given a Mac OS X Snow Leopard disk. However, when I tried to install it as a virtual OS for use on my computer, it refused to boot from the disk. If anyone knows how to boot through the disk, some help would be much appreciated; as I am currently out of ideas on how to make this work.

---

### Post by Helios747 on 2010-06-28
AFAIK OS X won't work in a VM.

however this article, written last May says yes. [http://hackaday.com/2010/05/03/virtualbox-beta-runs-mac-os-x/]("http://hackaday.com/2010/05/03/virtualbox-beta-runs-mac-os-x/")

they probably have new releases since then.

Are you using the Open Source (OSE version from synaptic)

or the closed sourced version, downloaded from Virtualbox website?

---

### Post by Tylerjd on 2010-06-28
There is a short and long answer to this question. 
Short: No
Long: Yes, but only on top of Mac OS X or Mac OS X server. In the hack-a-day article, they are running the VM on top of mac. Sorry, there is no way I know of that Mac OS X will run ontop of Ubuntu. check the support guide on the Sun/Oracle website.

---

### Post by rjcalifornia on 2010-06-28
try qEmulator...

---

### Post by nerdy_kid on 2010-06-28
i * heard * that qemu can be made to run os x, but that was a while ago and it was talking about the powerpc version of osx

---

### Post by lukeiamyourfather on 2010-06-28
VirtualBox 3.2.X or newer will support OS X guest out of the box ***if the host is also OS X***.

---

### Post by DoubleClicker on 2010-06-29
Running Mac OS X in a virtual machine is a direct violation of Apple EULA.  So, I would guess, that it would be against the ubuntu forum rules, to ask how to do it.

---

### Post by lukeiamyourfather on 2010-06-29
> **DoubleClicker said:**
> Running Mac OS X in a virtual machine is a direct violation of Apple EULA.  So, I would guess, that it would be against the ubuntu forum rules, to ask how to do it.

As long as the host is "genuine" Apple hardware its in accordance with the EULA, no?

---

### Post by DoubleClicker on 2010-06-30
> **lukeiamyourfather said:**
> As long as the host is "genuine" Apple hardware its in accordance with the EULA, no?

No,   you are not even allowed to run Mac OS X in a virtual machine, on top of Mac OS X on a genuine Mac.

---

### Post by lukeiamyourfather on 2010-07-01
> **DoubleClicker said:**
> No,   you are not even allowed to run Mac OS X in a virtual machine, on top of Mac OS X on a genuine Mac.

Wow, glad I don't use Mac at home! [-X

---

### Post by guidop on 2010-07-01
As far as I can tell, the English version of the OS X EULA only says it has to be installed on an Apple branded computer:

[http://www.apple.com/legal/sla/]("http://www.apple.com/legal/sla/") *

I don't see anything mentioning virtualization.

* Links to EULA .pdf documents are on this page.

---

### Post by josephe on 2010-08-30
Hi all 
Hope this doesn't violate any EULA or forum rules, but I'm looking into Mac and fully expect to be able to split my drive between Leopard, Ubuntu and Windows7. On a Macbook from what people have been saying this is fine, but not on say my other laptop which is a Dell.

But check this out, I know this relates to Windows machines, but if Windows, then why not Ubuntu

[http://www.taranfx.com/install-snow-leopard-virtualbox](http://www.taranfx.com/install-snow-leopard-virtualbox)

---

### Post by vishvesh on 2010-08-30
Hi josephe**,**
I was able to install Mac OS on virtual box. The steps provided in the links are correct.

---

### Post by dngfng on 2010-08-30
Regarding the EULA issue - this is a non-issue for Europeans as the EULA is void due to the fact that it is inside the Box - i.e. you are not able to read the EULA prior to purchase thus the EULA is null and void. At least over here in the old world.

---

