---
title: "Major Help // No Internet"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by Impsy on 2006-06-03
I got Xubuntu working on my old pc with windows 98, I used the alternate cd and got it installed. The next thing I did was follow a tutorial to get my serial mouse to work. Now I dont have sound and I also need help getting the floppy drive to work.. What do i need to install so i can get programs to work? someone said build-essentials or something.. I want to make these games that i got in tar.gz files to work.. this has been really confusing for me.

---

### Post by jdong on 2006-06-03
Whoo, you really sound like you have an *old* computer, and that's the reason why Xubuntu's been such a struggle. But hang in there, we'll get you up and running.


Some more information about your computer would be appreciated, especially on the hardware side.

 * What kind of sound card do you have? Does the volume control program seem to see any kind of sound card?
 * Can you open up a terminal, type "lspci", then paste us the results? This command tells us about most of the hardware inside your computer.

 * Use the Synaptic Package Manager to find the "mtools" package. You may have to turn on Universe under Repositories/Channels. Install it.
      * Insert a floppy, then at a terminal type "mdir A:". Does the floppy drive respond to that?

---

### Post by Impsy on 2006-06-03
I dont know how im gonna paste all the info, It says pretty much all Intel stuff plus a few ati things.. I think I have soundblaster. The synaptic couldn't find mtools. and terminal said mdir "is not a command" wow. nothing works.

---

### Post by jdong on 2006-06-03
Ok, your fundamental problem here is your lack of internet. I don't expect you to paste me that much information manually ;)


How do you typically connect to the Internet?

---

### Post by Impsy on 2006-06-03
Lol im using my downstairs computer, the one i installed Xubuntu to is upstairs and i *cannot* get internet on it at this time so im forced to do stuff manually. I want to get the right packages by floppy disk to it because i already burned like 200mb of linux games in tar.gz files.

---

### Post by jdong on 2006-06-03
By "cannot get internet" to it, do you mean it's a Xubuntu software problem (i.e. can't find/configure drivers) or a physical limitation of your computer setup?


The easiest way to do this is to get internet access so you can use Synaptic.

---

### Post by Impsy on 2006-06-03
I mean I dont have internet at all upstairs, Im getting a wireless router later this summer but that could be in a very long time. I actually want to do stuff with my computer for the time being although..

---

### Post by Impsy on 2006-06-03
so anyone help?

---

