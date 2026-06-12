---
title: "[SOLVED] the penguine got me....."
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by trigsenior on 2008-03-23
hello,

I have a little problem, i tryed ubuntu out on the live cd i loved it . I thought great il go and delete vista and install ubuntu , here come the problem it had already deleted my drive!!!!
I booted up into vista and there was the screen of death ..... my question how can i delete vista completly ? i don t mind deleting ubuntu aswell as i have no important files on it.

many thanxs for your help sory for my long question but .... They dont let me out much :lolflag:
only jk ....

---

### Post by Dr Small on 2008-03-23
Simply install Ubuntu over the entire disc and it will reformat Vista and place Ubuntu over the entire drive.

---

### Post by liquidfunk on 2008-03-23
Try booting from the LiveCD again, and just re-install Ubuntu, so that it takes up the whole HD.

---

### Post by Darganot on 2008-03-23
Just keep the 'use entire disk' option checked when you install ubuntu.  It should take over the entire Hard Disk that way and you can learn about partitions later, but it's not as hard as it might seem at first.

There's plenty of help available here, you just need to be specific in what you need help with.  :)

---

### Post by trigsenior on 2008-03-25
thanxs for all your help !
i used ticked the option of entire disk but it still come up , im starting to think this is not related to windows but is already on it if that makes sense ? which it does not to me ... 
It just says that its an intel computer .... and that hewlet packard is great , then it boots into linux .

---

### Post by philinux on 2008-03-25
When you say boots into linux do you mean the live cd or has it installed.

You should see 

Grub stage 1.5 loading 

if it's installed on your hard drive.

---

### Post by trigsenior on 2008-03-25
hello
yes it is installed on my hardrive i have no paritions . When it starts it goes to a blue boot screen then arfter a minute or less , if its a restart it can take up too 2 minutes then goes to the grub list .

---

### Post by stchman on 2008-03-25
> **trigsenior said:**
> hello,

I have a little problem, i tryed ubuntu out on the live cd i loved it . I thought great il go and delete vista and install ubuntu , here come the problem it had already deleted my drive!!!!
I booted up into vista and there was the screen of death ..... my question how can i delete vista completly ? i don t mind deleting ubuntu aswell as i have no important files on it.

many thanxs for your help sory for my long question but .... They dont let me out much :lolflag:
only jk ....

Install Ubuntu using the entire hard disc option.

---

### Post by trigsenior on 2008-03-25
hello but i did install under entire disk ....

---

### Post by joshrobinson on 2008-03-25
start up the live cd, open a terminal, and run 
```
sudo gparted
```

when it opens up, you should see your partition tables, right click and delete all partitions, so that it should say "unallocated space" or "unpartitioned space"

mind you this will clear your hard-drive of EVERYTHING, then apply the changes and close
then go about installing ubuntu as normal

---

### Post by trigsenior on 2008-03-26
hello ,

hmmm it just disapeared completly with out me doing anything .... witche craft ?
Im going to leave it and just hope it does not come back and bite me in the future .
Many thanxs for all your help :)

---

