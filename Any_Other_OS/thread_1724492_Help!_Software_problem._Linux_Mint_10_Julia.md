---
title: "Help! Software problem. Linux Mint 10 Julia"
date: 2011-04-08
forum: Any Other OS
---

### Post by Danzopop on 2011-04-08
Please help me!!!

I recently got Linux Mint 10 Julia, and greatly enjoy the user interface. But since I&#7743; a noob at programming, I am starting to grow grey hairs. In the Julia menu, you can search for software that people have made and shared. You can then download it straight from the menu and I haven´t had any problems before.

But now, a message saying;


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


pops up and honestly freaks me out. I tried doing the first option in terminal, but i didn really get further than the long list of commands.

Please helf me?

---

### Post by madmax75 on 2011-04-08
So giving this command in the terminal doesn't work?

```
sudo dpkg --configure -a
```What it does is that it tries to repair or reconfigure broken software packages or the package list, which has been mangled up at some point on your system.

What "long list of commands" do you get after giving this command in the terminal?

When the command runs, it might spit some info on what it is doing on the terminal window and then it will drop you back to the command prompt (which means that the command runs successfully). Maybe this is what you mean with "long list of commands"?

NOTE:

The

```
sudo dpkg --configure -a
```is the *only* part you have to write in the terminal... ;)

---

### Post by Dutch70 on 2011-04-08
Running that command in a terminal alone should solve the problem.
Edit: Looks like we were posting at the same time madmax :)

If not you may want to check the Linux Mint forums.
[[COLOR="Red"]http://forums.linuxmint.com/index.php?sid=3a97847ec2d1b432aadd4ca900f4f4fa[/COLOR]]("http://forums.linuxmint.com/index.php?sid=3a97847ec2d1b432aadd4ca900f4f4fa")

---

