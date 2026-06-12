---
title: "Internet Help!"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by Josh1 on 2006-01-09
Hello, I have a 'Motorola SB5100 Cable SURFBoard Modem', and the ethernet just wont work.. Its "seeing" that the card is there and whatever.. but it just wont work!

So, im going to try USB (What im using with Windows), and it wont show in network thing.
I found this on the internet, and a few other things, and this is what it said:
```

Log in as Administrator.
Open the /etc/modules file.
Add a line at the bottom with the following text: 92 CDCEther
Save the changes
Restart.

```
So how do i get to etc\modules? Sorry, im totally new to linux :)
Thanks,
Josh

---

### Post by kane_666 on 2006-01-09
to change directories you type:  cd /etc/modules
to get out of a directory type:   cd ..
to view a directory type            ls
that should help a bit

---

### Post by Greg2 on 2006-01-09
[QUOTE=Josh1]
So how do i get to etc\modules? Sorry, im totally new to linux :)[/QUOTE]
With terminal do:```
sudo gedit /etc/modules
```make your changes, save and close.

---

### Post by Thirsteh on 2006-01-09
/etc/modules is a file, you need to open it with your editor:

sudo gedit /etc/modules

Then add whatever needs to be added to the bottom of the file, save and close.

However, I doubt that "92 CDCEther" is what you should write, but oh well, try it out.

---

### Post by rooster on 2006-01-09
[QUOTE=Thirsteh]However, I doubt that "92 CDCEther" is what you should write, but oh well, try it out.[/QUOTE]

Oh yeah, give it a try and, please, post your results.

---

