---
title: "Problem starting up Partimage."
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by jorn on 2006-06-19
Hi!
Starting Partimage in terminal I got this message:
         
 /dev/dm inode doesn't exists.       
Partimage can create it for you.   
 You can also use the manual mknod   
 command. Do you want this inode     
 to be created for you now ?         
        
      Yes        No

I press Enter on "Yes" but nothing happens. When I create the folders and start Partimage again it says:/dev/dm is not a block device.

What's missing?

---

### Post by djsroknrol on 2006-06-19
I have an answer to that problem, as I had the same thing happen to me...in the GUI, it passed that message with a simple "no"...I'm not in front of that computer (at lunch at work), but I will post it when I get home....

---

### Post by djsroknrol on 2006-06-19
jorn...try this:

```
mknod -m 644 /dev/dm b 240 0
```

hope that helps you...it solved my problem with it....

---

### Post by jorn on 2006-06-20
Great, thank you, djsroknrol!

Have been searching here and there for a solution before I posted.
Now it seems that I can continue. I couldn't have worked that out by myself.
I even don't know what it meens, somebody does?

Greetings!

---

