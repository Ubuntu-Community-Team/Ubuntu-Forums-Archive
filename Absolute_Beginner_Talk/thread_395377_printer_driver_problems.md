---
title: "printer driver problems?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by monsterman on 2007-03-28
I have Ubuntu 6.06 and need drivers for canon i255 printer , searched the web and found driver on turbo site but when i try to open they seem to be debian drivers and will not open in ubuntu, 

this opensource stuff is frustrating for me I want to use it but if i get problems that i dont understand with drivers , I may have to go back to using evil empire stuff.

monsterman

---

### Post by ndefontenay on 2007-03-28
Hi.

There is a few things which will be frustrating if you don't understand where you're heading to.

When getting into the open source world, you have to realize that some companies simply don't support use well/not at all because we don't represent that big a market...yet.

That being said, the whole concept is to get things done with your Linux box at the centre of your mind.

So, the question to ask before buying a printer is: Ok, is it compatible with my Linux box. For instance, canon is not very famous for support Linux stuff...

This will be when you'll buy your next printer.

For your current printer, ubuntu is debian with a lot of easiness included.
So, it should be able to understand how to run .deb files.

If you get some errors while installing it, I suggest you post the error message wrapped in a code tag like this

```
This is some code
```

With this feedback, we'll try to think about a solution for you. And hopefully, later you will be able to help others with similar issues.

See you soon with your errors then : )

---

### Post by lwalper on 2007-03-28
I'm a newbie here too (I've got a lot of beans just because I've had a lot of questions), but you might try this command that was given to me:
```
sudo gdebi [insert your file name here -- without the brackets]
```

Can you navigate around at all in the **terminal**? You'll need to locate the file you downloaded. I've found that the default download location is the desktop. So, to navigate to your file open the terminal and type
```
cd Desktop/[folder name]
```
Note: omit the brackets when you type the folder name. Linux (Ubuntu) is also case sensitive -- if the file name has uppercase letters, you've got to use them. **D**esktop is not the same as **d**esktop.

---

