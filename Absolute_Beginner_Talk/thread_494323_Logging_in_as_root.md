---
title: "Logging in as root"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by sent17inel on 2007-07-06
Ok I'm always hearing how logging in as root is bad. And for the most part. I've completely ignored this. Ive used root for a long time and suffered the consequences of having to reinstall Linux about 5 times in the past month. But i have learned a bit. Anyways without flaming me on my ignorance please. Can you tell me a few things. First off i don't understand how when i create an account without root privileges i cant go into my menu and drag a program to my desktop. It wont let me. That seems ridiculous. Im just creating a shortcut. Or am i? anyways i don't like how i cant do that. I feel much more restricted in a normal account which is why i like logging in as root. I'm thinking about switching over to just using a normal account but i don't want to have to go into terminal to move files around or create new ones. not to mention that the only commands i know are mkdir and how to log in as sudo. Can someone plz enlighten me?

---

### Post by smoker on 2007-07-06
hi, if you're using ubuntu, you can give yourself temporary 'root' access by opening nautilus as root, ie, - alt+f2, then type 'gksudo nautilus' without the quotes.

or you can preclude a terminal command with the word 'sudo'

have a look here for good info: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by robertc36 on 2007-07-06
I have created accounts with admin privileges,.
So the behaviour you  describe doesn't sound right.
I have only been using linux 2 months now but i had access probs when compiling and got around this by using the chown command to give me write access to certain files folders.
As for the root thing i hear its bad so i am gonna believe that.
I found this helpful  [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by sent17inel on 2007-07-06
> **smoker said:**
> hi, if you're using ubuntu, you can give yourself temporary 'root' access by opening nautilus as root, ie, - alt+f2, then type 'gksudo nautilus' without the quotes.

or you can preclude a terminal command with the word 'sudo'

have a look here for good info: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Oh.................. So thats what that programs for! =)

---

### Post by Paul820 on 2007-07-06
You don't drap items to the desktop from the menu, you right click the program you want on the desktop, then click 'add this launcher to the desktop', otherwise it just glides back to where you dragged it from.

---

### Post by sent17inel on 2007-07-06
> **Paul820 said:**
> You don't drap items to the desktop from the menu, you right click the program you want on the desktop, then click 'add this launcher to the desktop', otherwise it just glides back to where you dragged it from.

I tried that and it doesnt work. I click add this launcher to the desktop and it doesnt add anything. And what exactly does nautilus allow me to do? i need something that will allow me to have the same powers as root all over my computer. Not just in that file browser thing. Gosh this is getting confusing.

---

### Post by Raineer on 2007-07-06
> **sent17inel said:**
> I tried that and it doesnt work. I click add this launcher to the desktop and it doesnt add anything. And what exactly does nautilus allow me to do? i need something that will allow me to have the same powers as root all over my computer. Not just in that file browser thing. Gosh this is getting confusing.

Not trying to flame you but you REALLY don't want that, it's inherent to the whole reason why Linux is more secure.  If you're going to do things that make you reinstall 5 times a month then maybe you should be finding out what you did instead of trying to get more access.

The reason you don't need 24/7 root access is that all those files you use daily should be under /home/$USERNAME, then you can do whatever you feel (including deleting every last one) and you can't break your machine.

---

### Post by smoker on 2007-07-06
> **sent17inel said:**
> I tried that and it doesnt work. I click add this launcher to the desktop and it doesnt add anything. And what exactly does nautilus allow me to do? i need something that will allow me to have the same powers as root all over my computer. Not just in that file browser thing. Gosh this is getting confusing.

a simple quick way - right click top panel, select 'add to panel', click 'application launcher' on top left, choose what app you want shortcut for, click 'add', then close. then drag the 'shortcut' from the panel to the desktop, you can then delete the panel shortcut.

---

### Post by sent17inel on 2007-07-06
I just had one of those oohhhhhhhhhhhh moments. But it came a bit to late. Im about to undergo a 6'th reinstall.... =( i always have to learn the hard way. But anyways let me tell u guys wut happened so u can laugh at me.... I used alt+F2 and that gksudo thing then i opened nautilus and scrolled up to the top of my directory and selected everything and right clicked it and went to properties and then  selected permisions and on ever box there i put create and delete and read and write access for everything. No idea wut happened from there but now im currently reinstalling windows xp and im going to dual boot it with ubuntu. Which is something i wanted to do anyways. But ya. Oh well. It happens........

---

