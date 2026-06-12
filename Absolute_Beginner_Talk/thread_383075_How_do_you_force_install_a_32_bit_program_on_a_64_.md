---
title: "How do you force install a 32 bit program on a 64 bit system?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-03-12
Hello,
What was the syntax for force installing a 32 bit program (picasa) on the 64 bit platform?

Thanks!

---

### Post by apjone on 2007-03-18
have a look for ia32-libs , it is a shared lib to allow 32/64 bit compatibility

FYI:


Q:  Will Picasa run on a 64-bit version of Linux?

Yes, but you&#8217;ll need to configure the system to provide 32-bit compatibility libraries.

Please refer to your Linux distribution&#8217;s help information for more on how to establish those libraries. On Debian, they come in a package called ia32-libs. 

[http://picasa.google.com/linux/faq.html#2](http://picasa.google.com/linux/faq.html#2)

---

### Post by marmaladejackson on 2007-03-18
HI there, thanks for the tip.  Found the 32 bit libs in synaptic, they were already installed.  When I attempt to intsall the .deb package, it gives an "Error: Wrong architecture 'i386'" message.  Is there something else I'm missing?
Thanks!
-B

---

### Post by apjone on 2007-03-18
I am not sure, even though i have 64bit AMD AM2 I opted for the 32 bit edgy so I havent come accross this, i just quoted what was on google's web site

---

### Post by shakma on 2007-04-11
I know the command, but I can't say if it'll make picasa work:

sudo dpkg --force-architecture -i <filename>.deb

That should do it.  It worked for me installing 32-bit wine on 64-bit edgy

Peace.

---

### Post by marmaladejackson on 2007-04-11
Thanks Shakma, that did it!!

-B

---

### Post by Inxsible on 2007-04-11
> **shakma said:**
> I know the command, but I can't say if it'll make picasa work:

sudo dpkg --force-architecture -i <filename>.deb

That should do it.  It worked for me installing 32-bit wine on 64-bit edgy

Peace.

Can you install any and all 32-bit software using that command onto a 64-bit OS ?

Also, does it provide any advantage over simply having a 32-bit OS installed. I ask because I have a 64-bit processor and was thinking of going for a 64-bit Linux distro instead of a 32-bit one.

---

