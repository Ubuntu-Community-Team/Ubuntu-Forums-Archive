---
title: "vmware question"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by tast01 on 2007-11-18
Hello im curious if this is possible. Right now im dual booting vista and gusty gibbon (each on separate  hard drives). Is it possible for me to install VMWARE on linux and run the already installed vista on that vmware?

---

### Post by oilchangeguy on 2007-11-18
> **tast01 said:**
> Hello im curious if this is possible. Right now im dual booting vista and gusty gibbon (each on separate  hard drives). Is it possible for me to install VMWARE on linux and run the already installed vista on that vmware?

nope. even a vm has to be a legal os.

---

### Post by tast01 on 2007-11-18
what do you mean by legal os?

---

### Post by oilchangeguy on 2007-11-18
> **tast01 said:**
> what do you mean by legal os?

ever hear that you can't use your windows product key on two different computers? a virtual machine is considered another computer.

---

### Post by ronmarley1 on 2007-11-19
> **oilchangeguy said:**
> ever hear that you can't use your windows product key on two different computers? a virtual machine is considered another computer.

What if the product key is a site license?  Before you post a smart-alek reply to a newbie in the Absolute Beginner Talk forum, be sure of the data.  
Additionally, I believe the OP is asking whether he can run the current install of Vista through VMWare, not make an additional installation of Vista in VMWare.
Please remember that this is the beginners area or the forums, and we would like to encourage new users.

---

### Post by oilchangeguy on 2007-11-19
> **ronmarley1 said:**
> What if the product key is a site license?  Before you post a smart-alek reply to a newbie in the Absolute Beginner Talk forum, be sure of the data.  
Additionally, I believe the OP is asking whether he can run the current install of Vista through VMWare, not make an additional installation of Vista in VMWare.
Please remember that this is the beginners area or the forums, and we would like to encourage new users.

what are you talking about? site license??????? i'm talking about the windows product key listed on the coa sticker on the computer. it's for that computer only. the user states they are dual booting, and want to know if they can run the ALREADY installed os as a virtual machine in ubuntu. and the answer is no.

---

### Post by pebo on 2007-11-19
To get back to the OP, maybe [vmware converter]("http://www.vmware.com/files/pdf/converter_datasheet.pdf") is worth a look ;)

---

### Post by asmiller-ke6seh on 2007-11-19
> **pebo said:**
> To get back to the OP, maybe [vmware converter]("http://www.vmware.com/files/pdf/converter_datasheet.pdf") is worth a look ;)

That looks neat! Yes, it looks like it might work.

---

### Post by Bushwack on 2007-11-19
I was able to get this working with VirtualBox (and Windows XP), but it wasn't easy.

See this thread in the VirtualBox forums (and the one linked from there) for the steps taken: [http://forums.virtualbox.org/viewtopic.php?t=2019](http://forums.virtualbox.org/viewtopic.php?t=2019)

---

### Post by ronmarley1 on 2007-11-19
> **oilchangeguy said:**
> what are you talking about? site license??????? i'm talking about the windows product key listed on the coa sticker on the computer. it's for that computer only. the user states they are dual booting, and want to know if they can run the ALREADY installed os as a virtual machine in ubuntu. and the answer is no.

A site license or volume license allows the owner to install a piece of software on multiple computers using the same product key.  For example, at my school, we have a volume site license for Windows, MS Office, Adobe Creative Suite, etc...  When installing Windows, we use one license key, and this can be used on up to 300 computers.  
This link: [http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=PXr&defl=en&q=define:site+license&sa=X&oi=glossary_definition&ct=title](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=PXr&defl=en&q=define:site+license&sa=X&oi=glossary_definition&ct=title)
has multiple definitions of a site license.

I was simply pointing out that the OP could conceivably install Vista again, if he is on a volume license, which you assumed he was not.  Additionally, Vista Enterprise, available to volume licensees only, allows the user to install Vista on one physical machine and up to four virtual machines, as long as the virtual machines are on the physical machine, and must be used by the same user.
I was also pointing out that your reply was somewhat acerbic for the beginners forum.

For example, I have Windows XP installed under VirtualBox using our volume license key.  The PC also dual boots Windows XP, under the same license.  You are correct, that does count as two installations.  However, I can install Windows using that key on up to 298 other PC's.

---

