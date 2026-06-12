---
title: "removing older kernels"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-10-16
I have been using ubuntu since the hoary hedgehog release and everytime that I upgrade to the new distribution I get another entry added to my grub.lst file. I don't like to have a lot of options listed on my grub screen on boot up so I just commented them out so I don't have to see them. I just keep the latest kernel entry along with my windows entry. My question is, would the rest of the system be ok if I decide to remove the older kernels and would it be an ok to do that? How could I remove the older kernels from my system?

---

### Post by bulldog on 2006-10-16
Look in synaptic for linux-image ******* and remove the ones wich you don't uese anymore.

Be carefull to keep at least one :D

---

### Post by era86 on 2006-10-16
just edit your /boot/grub/menu.lst file and remove the entries you no longer need. you should be able to figure it out once you see the contents of the file

---

### Post by bulldog on 2006-10-16
> **era86 said:**
> just edit your /boot/grub/menu.lst file and remove the entries you no longer need. you should be able to figure it out once you see the contents of the file

And if you get a kernel updat you have to go all over again :D 

Just use synaptic and remove the old ones,free's up some space too.

---

### Post by grim918 on 2006-10-16
> just edit your /boot/grub/menu.lst file and remove the entries you no longer need. you should be able to figure it out once you see the contents of the file


I have edited my grub.lst file. I want to remove them so that I can free up some disk space. I was just wondering if that would cause some problems if I do that. I will remove them using synaptic. I hope all goes well, and yes I will keep at least one.

---

### Post by bulldog on 2006-10-16
> **grim918 said:**
> I have edited my grub.lst file. I want to remove them so that I can free up some disk space. I was just wondering if that would cause some problems if I do that. I will remove them using synaptic. I hope all goes well, and yes I will keep at least one.

There should be no problem,did it several times myself.

Goodluck anyway.

---

### Post by Mimsy on 2006-10-16
Okay, fascinated newbie question, based on "be careful to keep at least one".

Would Synaptic actually be able to do that? Wouldn't the act of running the OS, and using an application within it, prevent the kernel from being removed, since it's being used at the time?

Or did I just prove all over again how naive and ignorant I am...? :)

/Mimsy

---

### Post by bulldog on 2006-10-16
> **Mimsy said:**
> Okay, fascinated newbie question, based on "be careful to keep at least one".

Would Synaptic actually be able to do that? Wouldn't the act of running the OS, and using an application within it, prevent the kernel from being removed, since it's being used at the time?

Or did I just prove all over again how naive and ignorant I am...? :)

/Mimsy

Never tried do remove them all,and I'm sure I never will :D :D 

Imagine it works and your kernels are destroyed](*,)

---

### Post by Mimsy on 2006-10-16
> **bulldog said:**
> Imagine it works and your kernels are destroyed](*,)

...

Then I would have to reinstall everything. That would be very inconvenient. ](*,) 

Maybe I can try it if I need to do a full reinstall for other reasons? :-D 

/Mimsy

---

### Post by grim918 on 2006-10-16
I never thought of that. I should try it some day to see if it would actaully do it.

---

### Post by bulldog on 2006-10-16
Let us know if you can remove them all.

Interresting question though.

---

### Post by Mimsy on 2006-10-16
I have created a monster....! :shock: 

/Mimsy

---

### Post by bulldog on 2006-10-16
> **Mimsy said:**
> I have created a monster....! :shock: 

/Mimsy

Yep,you're guilty......:D

---

### Post by Mimsy on 2006-10-16
The very sad thing is that I'm so fascinated by software, and how it works, and by Linux especially, that I might actually try it when I get home tonight, just to see what happens... :twisted: 

AFTER I've made a new backup, so I don't lose my resume all over again.

/Mimsy

---

