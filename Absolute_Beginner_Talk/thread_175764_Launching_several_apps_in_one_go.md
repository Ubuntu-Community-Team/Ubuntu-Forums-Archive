---
title: "Launching several apps in one go"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by phatdad on 2006-05-13
Can anyone point me in the right direction for a 'How To' covering writting programs or routines in Ubuntu?
I'd like to create a launcher type thing that will start Firestarter, Connect via startadsl, then start Firefox in a single click.
Is there a way to get the standard launcher to da this? Or does it only handle one app at a time?

---

### Post by johnnymac on 2006-05-13
The simplest approach would be just to write a script that executes all you want it to and then create a panel icon that points to the script.  When clicked the icon will cause the script to get executed and POOF - all you stuff launches.

---

### Post by phatdad on 2006-05-13
Thanks for the help, but showing my lack of know how, I have to ask how you go about writting a script.

---

### Post by Omnios on 2006-05-13
Here is a tutorial on shell scripts.

 [http://www.tldp.org/LDP/Bash-Beginners-Guide/html/chap_02.html]("http://www.tldp.org/LDP/Bash-Beginners-Guide/html/chap_02.html")

---

### Post by phatdad on 2006-05-13
Many thanks, off to have a go now.

---

### Post by Kvark on 2006-05-13
Firestarter is a tool for controlling [iptables]("http://en.wikipedia.org/wiki/Iptables") which is a firewall that is built into the kernel and is always running. So you don't need to have Firestarter running to be secure since it is not the actual firewall. Ok, maybe you want it to monitor attacks or something which might be fun but pointless since they don't get in anyway.

As for the script, all commands are the same in scripts as in the terminal. So start the programs from a terminal. Type down the exact commands you used in a text file and add a line that says "#!/bin/bash" at the top. Save it as something that ends with ".sh" and make the file executable with "chmod +x file.sh". Then make a custom launcher that points to the file.

For example to start xmms, firefox and xchat, the file would look like this:
```
#!/bin/bash
xmms &
firefox &
xchat &
```
The & at the end of the lines makes sure the script doesn't have to wait for the first program to close before starting the next. Another use is to type "gedit file.txt &" so it doesn't tie up the terminal until you are done.

---

### Post by phatdad on 2006-05-13
Thanks again. I've just been driving myself mad, loads of 'not that you fool' beeps coming out of my box.
Back soon when I get this going

---

### Post by phatdad on 2006-05-13
Got that going, but, call me paranoid if you will, I would be happier seeing that Firewall is working OK. When running, Firestarter reports blocking 'serious' attempts. Will I have the same protection without the GUI bit? Guess this is a former windows user point of view......:confused:

---

### Post by Omnios on 2006-05-13
Actualy Firestarter is a graphical front end for ip tables which runs even without the front end so even so you are still protected but will not get the warnings. Personaly I feel safer having it to show what is happening.

---

