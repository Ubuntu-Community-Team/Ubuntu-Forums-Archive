---
title: "Need help with graphics card, and dial-up"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by veryconfused on 2007-06-13
Hello, i just recently installed ubuntu, i am currently on windows because i cant seem to get ubuntu to work, im actually having two problems, one is, i think it cant read my Nvidia graphics card, becuase it wont let me change screen res. above 800x200-(or near that), nad same with the refresh rate. my second one is im currently using dial-up, and i cant seem to find a place to put my dial-up setting and beggin using my internet on ubuntu, any help is appreciated, Thank You.

---

### Post by Inxsible on 2007-06-13
Have you tried installing the restricted NVidia drivers?
 
or you might have to change your xorg.conf file. Post back the output of the following command:
 
```
gedit /etc/X11/xorg.conf
```

---

### Post by veryconfused on 2007-06-13
Sorry im very nooby, have no clue what you just told me to do, could you explain it?

---

### Post by Inxsible on 2007-06-13
When you first log into Ubuntu, does it give you a message to install the restricted NVidia drivers. probably in the upper right corner, near the system clock you get an icon.
 
If not, you can go to System --> Administration --> Restricted Drivers
 or is it System --> Preferences --> Restricted Drivers
 
or something to that effect. Sorry I am not on my Ubuntu machine right now.

---

### Post by veryconfused on 2007-06-13
ive tried that, i click to enable it, and it diddnt enable it, very weird. but yea it was in the restriscted drivers.

---

### Post by autocrosser on 2007-06-13
OK--in easier terms--look at your Menu>Applications>Terminal. open up a terminal & gedit /etc/X11/xorg.conf then hit return. You'll see a bunch of code--we need to see it to be able to help you. You could copy/paste it into a text doc & put it on a floppy, then go into windoze & copy it to the forum.
 
As far as the dial-up issue--I'm at work right now & I'll be available to help in about 5/6hrs....

---

### Post by veryconfused on 2007-06-13
But is that my problem? is that why it looks very crappy, and i cant change my back ground, screen res, and screen rate?

---

### Post by veryconfused on 2007-06-13
Sorry to bother you, do you have a IM were i can contact you later? also were is the return key.

---

### Post by autocrosser on 2007-06-13
YES-you need the restricted driver to open you card "up"... You will most likely need internet access to download the driver if it was not installed.....

---

### Post by veryconfused on 2007-06-13
Well, thats my second problem, internet, dont currently have fast internet access all i have is dial-up, which id probly need a driver download for it to, so am i stuck? is that it?

---

### Post by autocrosser on 2007-06-13
Sorry--I need to get back to work---I'm available on the forums only---Watch for me in about 5/6hrs..  (return is the "enter"key)

---

### Post by veryconfused on 2007-06-13
Some one else help me, please.

---

### Post by veryconfused on 2007-06-13
Any help?

---

### Post by veryconfused on 2007-06-13
Need help.

---

### Post by veryconfused on 2007-06-13
Some help me!!!!

---

