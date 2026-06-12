---
title: "Terminal trouble"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by mikealso on 2007-01-27
Hi I'm mike a beginner in Linux.  I loaded Ubuntu successfully and most things seem to be working, except the terminal.  I'm using a command given in "The Official Ubuntu Book" i.e. foo@bar~$ 1s and when I enter this I get the following -
bash: foo@bar~$: command not found
What am I doing wrong?

---

### Post by BarfBag on 2007-01-27
> **mikealso said:**
> Hi I'm mike a beginner in Linux.  I loaded Ubuntu successfully and most things seem to be working, except the terminal.  I'm using a command given in "The Official Ubuntu Book" i.e. foo@bar~$ 1s and when I enter this I get the following -
bash: foo@bar~$: command not found
What am I doing wrong?

Do you mean ls?  You must've misread the font on the page.

---

### Post by Iarwain ben-adar on 2007-01-27
Hiya mikealso,

Welcome to the forum! Hope you will enjoy Ubuntu as much as i do :D


Just for the reference, that is not a command :)

That is how your terminal looks like.

This is mine, so you know it's kinda standard.
Everything past the : is command. Everything in front of it, is you user@pc-name and the folder you're in. (~ is your /home/mikealso folder)


Iarwain

---

### Post by PrinceArithon on 2007-01-27
Oh yes a n00b mistake for sure, but don't be let down by it at all.  Let me exlain something.

In the book you see "foo@bar~$".  All of this means something.

The "foo" in all of what you see is his user name.  The "bar" is his computer's name.

Now here is for the other parts.

the "~" means you are in your home directory or root directory.  The "$" is about the only thing I can't explain.  All I can say is it is always at the end of that whole part in the terminal.

So when you are using your Terminal, you never put "foo@bar~$" in for a command.  It is just part of the name and location.

Now for your "1s".  With the font in any Linux system the lower case L looks a little odd.  I guess it does look like a 1.  Go into your terminal and type in the lower case L and see how it looks.  You'll see that it looks the same as in the book.

So your command is "ls" not "1s".

If you have any other questions just go ahead and ask.

---

### Post by mikealso on 2007-01-28
> **BarfBag said:**
> Do you mean ls?  You must've misread the font on the page.

Thanks All, maybe I should read all of the book

---

### Post by nhandler on 2007-01-28
> **PrinceArithon said:**
> Oh yes a n00b mistake for sure, but don't be let down by it at all.  Let me exlain something.

In the book you see "foo@bar~$".  All of this means something.

The "foo" in all of what you see is his user name.  The "bar" is his computer's name.

Now here is for the other parts.

the "~" means you are in your home directory or root directory.  The "$" is about the only thing I can't explain.  All I can say is it is always at the end of that whole part in the terminal.

So when you are using your Terminal, you never put "foo@bar~$" in for a command.  It is just part of the name and location.

Now for your "1s".  With the font in any Linux system the lower case L looks a little odd.  I guess it does look like a 1.  Go into your terminal and type in the lower case L and see how it looks.  You'll see that it looks the same as in the book.

So your command is "ls" not "1s".

If you have any other questions just go ahead and ask.

The $ at the end of "foo@bar~$" simply means that you are in a user terminal. Sometimes, you might see this instead "foo@bar~#" that means that it is a root terminal. You use "sudo" in front of commands to execute them as root.

---

### Post by PrinceArithon on 2007-01-28
AH HA now I know what that all means.  After all this time I finally know.  I will try to keep it in mind.

Yes Mike, keep reading the book, it's a good book.  There is a lot you can learn from it.

---

