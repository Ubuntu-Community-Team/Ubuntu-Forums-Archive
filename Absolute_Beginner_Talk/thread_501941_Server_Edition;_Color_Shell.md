---
title: "Server Edition; Color Shell"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Ek0nomik on 2007-07-15
I just installed the Server edition of Ubuntu.  I was running my server on the Desktop edition before, and I decided it was time to move to just a command line interface.

When I ran a search, I noticed folders showing up in the color green.  In the Desktop edition, I have my username and desktop name colored.  Can you do that with the Server edition?

I know I could just control it via SSH, but I was just curious.  Thanks!

---

### Post by 5-HT on 2007-07-16
Yup, just need to edit your PS1 environmental variable. One way would be to do it in ~/.bashrc. There should already be a colourized prompt there that's commented out. Simply uncomment it (remove the #'s) and comment the other PS1 line. 
If you want to customize your PS1: [http://www.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www.ibm.com/developerworks/linux/library/l-tip-prompt/)

cheers,

---

### Post by Ek0nomik on 2007-07-16
Thanks 5-HT.

I actually managed to get that far last night.  Now what I am looking to do is specify custom colors.  Is it possible to get custom colors as opposed to the default green and light green, red and light red, etc?

The colors are so bold they kinda hurt my eyes.  ;)

---

