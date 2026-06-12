---
title: "Wireless networking: How to connect using the terminal?"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by kkjaergaard on 2007-09-19
How do I connect to the AP's at school using the terminal?

They use some PEAP-MSCHAPV2 authentification (with dymanic assigned WEP-keys), but I'm quite sure I've configured xsupplicant correctly for this.

So, how do I connect to the network *and* use xsupplicant using the terminal?

---

### Post by reckless2k2 on 2007-09-19
```
sudo ifup 
```


would be for networking. i'm not sure about the supplicant.

---

### Post by kkjaergaard on 2007-09-24
> **reckless2k2 said:**
> ```
sudo ifup 
```


would be for networking. i'm not sure about the supplicant.

Can you give me a little more detailed explanation or provide a link to a tutorial or something like that?

---

### Post by reckless2k2 on 2007-09-24
well if you have configured everything then 

```
sudo ifup 
```


from the terminal will bring the interface up. maybe i'm misunderstanding what you need but i thought it was how to start the interface from the terminal.

---

### Post by kkjaergaard on 2007-09-25
> **reckless2k2 said:**
> well if you have configured everything then 
```
sudo ifup 
```
from the terminal will bring the interface up. maybe i'm misunderstanding what you need but i thought it was how to start the interface from the terminal.

I think I haven't configured everything then. I get this reply:

```
$ sudo ifup
ifup: Use --help for help

```

---

### Post by stillingen on 2007-09-25
Have a look at iwconfig. This is the equivalent to ifconfig for wired interfaces. Do 'man iwconfig' for instructions of use, which is also available [ **here** ](http://www.linuxcommand.org/man_pages/iwconfig8.html)

---

### Post by reckless2k2 on 2007-09-25
when i was bugging around in the terminal a lot on 5.04 and 5.10, i just wrote a quick bash script to bring up the interface quite easily. rather than typing multiple commands i'd just run one bash script and be up in one time. i don't know if you are looking in this direction or not. i guess i don't understand the need to connect using the terminal.

---

### Post by kkjaergaard on 2007-09-25
> **reckless2k2 said:**
> when i was bugging around in the terminal a lot on 5.04 and 5.10, i just wrote a quick bash script to bring up the interface quite easily. rather than typing multiple commands i'd just run one bash script and be up in one time. i don't know if you are looking in this direction or not. i guess i don't understand the need to connect using the terminal.

Well, I'm not sure I need to connect using the terminal. But I need to use xsupplicant and I'm quite sure it doesn't work with the GUI connector in Gnome.

If I need to use the terminal and if I find out how to connect, I will properly also write a script like you wrote.

---

