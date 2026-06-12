---
title: "How to make bashscripts"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-11-19
okay how do i make like alias bash scripts that start when i open the gnometerminal and how can i make it show the output in the terminal

---

### Post by llamakc on 2007-11-19
Give an example as to what you want. There's more than one way to do this sort of stuff.

---

### Post by fedex1993 on 2007-11-19
where it draws like a ubuntu logo and then says helleo to $user

---

### Post by llamakc on 2007-11-19
For one user or all of them?

---

### Post by fedex1993 on 2007-11-19
just for one user.

---

### Post by llamakc on 2007-11-19
Do you have more than one user on the machine? Doing it this way is the simplest.

---

### Post by fedex1993 on 2007-11-19
nope just me and my lonely personal laptop. well if you want to include the root account which i dont think any user uses

---

### Post by llamakc on 2007-11-19
Cool. You want to edit the file /etc/motd.tail.

```

sudo gedit /etc/motd.tail

```

Shoot, I just realized that works for command-line only. I don't think Gnome-Terminal reads from there.

Do you want this EACH time you start the terminal from the menu?

---

### Post by fedex1993 on 2007-11-19
well can i just create a laucher that runs a bash script?

---

### Post by Dr Small on 2007-11-19
If you have figlet installed, you could do this:
```
#!/bin/bash
figlet "ubuntu";echo -n 'Hello '; whoami
```

Dr Small

---

### Post by llamakc on 2007-11-19
> **fedex1993 said:**
> well can i just create a laucher that runs a bash script?

Yes. I asked HOW you wanted it displayed, and from what program.

---

### Post by fedex1993 on 2007-11-19
okay all i want is like a text that is in the shape and color of the ubuntu logo to start up with a custom launcher that i could use everytime the terminal is started. I can install someother kind of terminal that reads from /etc/motd.tail

---

### Post by Dr Small on 2007-11-19
did anyone read my post before it got pushed to page 1 ?

---

### Post by fedex1993 on 2007-11-19
> **Dr Small said:**
> did anyone read my post before it got pushed to page 1 ?
Umm you mean page 2 and i dont know what fdget or what ever the program is called

---

### Post by Dr Small on 2007-11-19
Install it, and it draws ascii art, of of text that you input, so it could draw "ubuntu" in the terminal and look like ascii image.

```
sudo apt-get install figlet
```

---

### Post by llamakc on 2007-11-19
Another nifty one is called "toilet".

---

### Post by Dr Small on 2007-11-19
If you want to try it out, install figlet, as mentioned above, edit .bashrc and add the following line to the end of the file. This will output the string at the beginning of every terminal that you open:
```
figlet "ubuntu";echo -n 'Hello '; whoami; echo ''
```

I just tried it, and it works great ;)

---

### Post by fedex1993 on 2007-11-19
> **Dr Small said:**
> If you want to try it out, install figlet, as mentioned above, edit .bashrc and add the following line to the end of the file. This will output the string at the beginning of every terminal that you open:
```
figlet "ubuntu";echo -n 'Hello '; whoami; echo ''
```

I just tried it, and it works great ;)

where is the .bashrc located or do i need to create one

---

### Post by llamakc on 2007-11-19
In your home directory ~

```

gedit ~/.bashrc

```

---

### Post by Dr Small on 2007-11-19
And for the sake of simplicity :D
[http://php.8ez.com/drsmall/blog/?p=164](http://php.8ez.com/drsmall/blog/?p=164)

---

### Post by fedex1993 on 2007-11-19
ty very much works perfectly is there anyway that i can get the ubuntu colored like orange and yellow or something like that

---

### Post by Dr Small on 2007-11-19
I have no idea about colors in the terminal. So I can't answer that question.

---

### Post by fedex1993 on 2007-11-19
ahh okay thanks for atleast helping me get this working thank you

---

