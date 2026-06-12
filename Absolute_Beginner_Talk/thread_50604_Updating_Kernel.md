---
title: "Updating Kernel"
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by ozzie123 on 2005-07-20
Hello,

I'm not quite sure where should I put this but I'll shoot anyway.

Can we update our kernel using apt-get? If so, is there any special command I have to execute?

Thanks

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=ozzie123]
Can we update our kernel using apt-get? If so, is there any special command I have to execute?[/QUOTE]

What exactly are you asking:

Can I get the smp (multiprocessor for hyper threading) or 686 kernel in synaptic? 

Yes.

Can I get the newest version kernel in synpatic?

Yes, but that involves upgrading to Breezy, which will bring more stability problems then its worth. Breakage will come, its a promise.

Can I upgrade Hoary's kernel to the newest version in Synaptic?

No. Backports won't touch the kernel, ubuntu fans only get new kernels when they compile them themselves or when a new release comes.

I hope I answered your question.

---

### Post by UbuWu on 2005-07-20
[QUOTE=ozzie123]
Can we update our kernel using apt-get? If so, is there any special command I have to execute?[/QUOTE]

In case you are wondering: apt-get can handle kernel updates, the only differences with other packages is that the old kernel will also remain on the system (you can remove it manually once you have verified the new kernel works ok) and you will have to reboot to use the new kernel.

---

### Post by ozzie123 on 2005-07-20
Ah I see...

Well, it's better to stay on Hoary's default kernel just a little bit :)

---

### Post by odin on 2005-07-21
Hi  everyone!!!

Can anyone tell me what do I have to remove when I want to remove old kernels?
I just upgraded to hoary and the warty kernel is still with me nad another that I compiled to adapt it better to my system so I have like 3 or 4 :grin: 

My question is about the name of the files(I dont know if its vmlinuz or any otrher thing)

Thank's

---

