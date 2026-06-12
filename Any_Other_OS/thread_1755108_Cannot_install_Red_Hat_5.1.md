---
title: "Cannot install Red Hat 5.1"
date: 2011-05-10
forum: Any Other OS
---

### Post by slashwannabe94 on 2011-05-10
Hello all, i managed to come across to genuine Red Linux 5.1 cd's today and have tried installing it. I have a the book that accompanies these discs but have ran into errors not mentioned in the book. 
See screenshot

---

### Post by wojox on 2011-05-10
It looks like your trying to install 64 bit RHEL on a 32 bit system.

---

### Post by slashwannabe94 on 2011-05-10
> **wojox said:**
> It looks like your trying to install 64 bit RHEL on a 32 bit system.

I'm sorry correct me if i am wrong but isn't that impossible? Considering the minimum RAM requirement for Red Hat Linux 5.1 is only 2MB of RAM? 

I'm doing this through a virtual machine, it has 8MB of RAM. 

My CPU architecture on the host machine is i686. Could that be the problem?

---

### Post by wojox on 2011-05-11
> **slashwannabe94 said:**
> I'm sorry correct me if i am wrong but isn't that impossible? 

My CPU architecture on the host machine is i686. Could that be the problem?

i686 is 32 bit

x86-64 is 64 bit

What arch is Red Hat?

---

### Post by Spice Weasel on 2011-05-11
AMD64 was only announced in 1999 and Red Hat 5.1 was released in 1998, so I doubt that is the issue. If the installer runs, the OS is the right arch. There is something wrong with the CD. Either it's corrupted, or includes packages of mixed architecture for whatever reason.

---

### Post by wojox on 2011-05-11
> **Spice Weasel said:**
> If the installer runs, the OS is the right arch.

I forgot about that. It wouldn't even boot if that were the case. 

Does it ask you for a Server and a Path and is it set correctly? How far into the install do you get before this screen comes up?

---

### Post by slashwannabe94 on 2011-05-11
> **wojox said:**
> i686 is 32 bit

x86-64 is 64 bit

What arch is Red Hat?

Red Hat is i386. Is it possible to fake the CPU architecture in the virtual machine?

---

### Post by slashwannabe94 on 2011-05-11
Hmmm this is turning out to be quite a conundrum haha. I will try adding and removing different packages.

---

### Post by snowpine on 2011-05-11
Red Hat 5.1 is very old; you can purchase the latest release from [http://redhat.com](http://redhat.com)

If you prefer a free, community "clone" you can use [http://centos.org](http://centos.org)

---

### Post by wojox on 2011-05-11
> **slashwannabe94 said:**
> Red Hat is i386. Is it possible to fake the CPU architecture in the virtual machine?

Your i686 cpu should be able to run i386. So that's weird. For what it's worth since there is no support for it, you should take snowpine's advice and install CentOS. I've run it as well and it's pretty solid and free.

---

### Post by eolson on 2011-05-11
I'm afraid I won't be of much help,  but I ran Red Hat 5 (and 4) on an old Pentium II (I think, my memory ain't what it used to be, things fade out after 68 years or so).  But anyway, it installed and ran just fine, with no hitches.  The only thing was the mount points which seem simple today.  I switched to mandrake (now mandriva) not too long after as I remember.

---

### Post by slashwannabe94 on 2011-05-11
Thanks quite helpful actually man :), thank you. 
I have downloaded CentOS 5. How alike is it to RedHat Linux? i.e. the types of package maintainers, shells, etc? 

Thanks, 
SlashWannabe94

---

### Post by jeffathehutt on 2011-05-11
Redhat 5.1 is very different than the Redhat of today.  Centos is very similar to modern Redhat, not necessarily Redhat 5.1.  Basically, Centos takes all the packages from Redhat, recompiles them and then distributes them for free.  Today, Redhat enterprise is very expensive because it is meant for businesses and other enterprise customers.

Redhat 5.1 would be closer to Fedora today.  Many years ago, Redhat sort of split, leaving Redhat enterprise and Fedora, which was the community supported version sponsored by Redhat.

As to the errors installing 5.1, I have no idea...:-k

---

### Post by snowpine on 2011-05-12
> **slashwannabe94 said:**
> Thanks quite helpful actually man :), thank you. 
I have downloaded CentOS 5. How alike is it to RedHat Linux? i.e. the types of package maintainers, shells, etc? 

Thanks, 
SlashWannabe94

CentOS 5.6 is 100% binary compatible with Red Hat Enterprise Linux 5.6. The only differences are removal of Red Hat branding/artwork and lack of official Red Hat paid support. Have you visited the CentOS website and read their FAQs, forum, etc?

---

### Post by slashwannabe94 on 2011-05-12
I have downloaded and installed RedHat Linux on my virtual machine. I'm happy with the o/s but not entirely sure on it's relevance to the book i bought. Either way it's still a cool operating system and looks quite... "groovy" ;) 

Thanks allot guys, 
SlashWannabe94

---

