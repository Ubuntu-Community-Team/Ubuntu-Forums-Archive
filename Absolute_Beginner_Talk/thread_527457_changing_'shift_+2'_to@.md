---
title: "changing 'shift +2' to@"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by struggling beginner on 2007-08-16
New install of 7.04. Minutes old.

When configuring email, shift + 2 gives me quotation marks instead of @ sign. Read about fix using terminal. Typed in sudo.......blah blah. Asks for password on next line, but won't accept keystrokes to enter password.

---

### Post by chrisN_uk on 2007-08-16
Don't know about the password thing but to change your keyboard setup graphically, click 
system -> preferences -> keyboard -> layout. 
It sounds like you've got it set up as U.S. and you want U.K.

---

### Post by Arthur Archnix on 2007-08-16
Sounds like a keyboard configuration error. 

I'd do this first, then try to change the keyboard configuation:

1 Open up a notepad, text editor or something. And once open type out your password. Write down what you see on a piece of paper.

2. Go to system, preferences, and choose keyboard. Under layouts you need to add your keyboard layout. If you're in north america you'll probably want to choose us-english and then check the box to set it as default.

---

### Post by coffeecat on 2007-08-16
> **struggling beginner said:**
> Asks for password on next line, but won't accept keystrokes to enter password.

<panto-mode> Oh, yes it does! </panto-mode> :wink:

This often confuses people new to Linux. When you type your password in a terminal, you don't get any visual feedback - no stars or anything. But don't worry - it's going in. Just type the password and then <enter> and your password should be accepted.

I agree with the other posters about the 2/@ business. You've got a US/UK keyboard thing going there. The @ and " symbols are transposed between UK and US keyboards, but just to complicate things the UK Mac keyboard has @ and " in the US PC keyboard positions. :? I'm typing on a Mac keyboard in Gentoo atm (Don't ask!) and it gets very confusing at times.

---

### Post by mali2297 on 2007-08-16
Your problem might be related to this:
[http://ubuntuforums.org/showthread.php?t=480498]("http://ubuntuforums.org/showthread.php?t=480498")

---

### Post by struggling beginner on 2007-08-16
Changing the keyboard layout back to US English did it.

Thank you all very much.

The entering password in terminal advice wasn't needed after changing the keyboard layout, but it will be remembered. 

tyvm

---

