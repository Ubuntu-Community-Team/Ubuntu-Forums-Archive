---
title: "Picasa problems"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by OldGrey on 2007-03-26
Hi

I have managed to install Picasa 2 and it works fine in my log in but for the others it comes up with an error message and states that I must run the following as root:

"chmod 666 /devnvidia0 /dev/nvidiaiact1"

1 at the risk of appearing really ignorant how do I run it as root?
2 why will Picassa only work on my log in?

Help will be greatly appreciated

OldGrey

---

### Post by tipsqueal on 2007-03-27
To run it as root just type

"sudo chmod 666 /devnvidia0 /dev/nvidiaiact1"

When prompted type in your administrator account password, which is the account that Picasa can run on. It only works on your login because you have not set the privileges correctly, running that command will allow it to be run on the other logins.

Hopefully I've been able to help you.

---

### Post by OldGrey on 2007-03-28
I had typed the command incorrectly, but once that was sorted it did the trick

Thanks for you help

OldGrey

---

### Post by Mark Haysom on 2007-05-16
Hi,

Not sure if its correct to add to this thread, so apologies if its wrong.

The chmod 666 on the two mentioned files does allow other users to run Picasa in there own home areas. However I have found that when you next boot linux you are back to square 1 having to issuse the chmod command all over again. Is there a way around this? (sorry new to linux, but learning fast) as I want other people to use the computer when I am not around to issuse the sudo chmod command.

---

