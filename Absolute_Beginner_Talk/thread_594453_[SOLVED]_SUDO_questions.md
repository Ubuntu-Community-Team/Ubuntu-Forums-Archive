---
title: "[SOLVED] SUDO questions"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by gobuntu on 2007-10-28
Dear friends,

I used sudo -i and it did what I needed.

So, how do I sudo-out when no longer needed?

In other words, how do I un-SUDO so I get back my previous shell-prompt?

In addition, while I could not "sudo-out", I typed at the shell:

man sudo

to investigate this question, and I did get the sudo manual, which did not resolve my question.

But then, I could not get out of the manual, for,  the last line I can read is "END" and could not figure out how to release back to the shell from there.

So this is like two questions in one, but related.

Thanks for any help.

---

### Post by aidanr on 2007-10-28
exit
q

---

### Post by Six_Digits on 2007-10-28
There is no need to "un-sudo". As for the manual, have you tried clicking "X"?

---

### Post by Crafty Kisses on 2007-10-28
> **Six_Digits said:**
> There is no need to "un-sudo".

Nope, not really.

---

### Post by andhar on 2007-10-28
doesnt the sudo automatically give u a time limit on how long u are superuser for? 

unless youre actually root it should return you to a normal user if you are "root@**" you can type exit. 

I set the root password so I can log in at "su" instead of sudo.

---

### Post by gobuntu on 2007-10-28
Dear friends,

Well, I know that EXIT and Click X closes the terminal, and I can even close it with CTRL-D

However, my question relates to NOT HAVING to close the terminal, as I would like to leave the MANUAL that "man sudo" brings.

By the way, when the SUDO MANUAL appears, the last line, by scrolling reads:

" Manual page sudo(8) line 367/391 (END)"

and what I am asking is how to LEAVE THAT MANUAL and get back to the shell prompt.

Also, if there were no need to "un-sudo" or "sudo-out", why then is there a need to SUDO?

We might as well be SUDO all time.

I realize that there are time limits to sudo, but there is also the K parameter that can Kll the time limit, according to the manual I just read.

And, WHY should one be forced to X (close) the terminal if one is not done with using it?

Remember, SUDO is supposed to be TEMPORARY, so IS THERE as sudo-out  or not?

Thanks for any replies.

---

### Post by aidanr on 2007-10-28
Dude I already told you type **exit** to "sudo-out" after running sudo -i and hit **q** to exit manpages

---

### Post by meindian523 on 2007-10-28
gobuntu:

Ans to question 1:

How to sudo-out:Ctrl+D to logout of sudo and back to your prompt wherein if you press Ctrl+D again,you dismiss the terminal....or if you want to continue with some commands in the terminal,simply don't press Ctrl+D the second time.....

Ans to question 2:

How to quit the manual page:You can quit the manual page by pressing q which will drop you back to whichever prompt you invoked the manual page from.And not necessary that you can quit only at the end,you can press q to exit the manual page at any line you wish......

Hope that helps.......:)

---

### Post by gobuntu on 2007-10-28
> **aidanr said:**
> Dude I already told you type **exit** to "sudo-out" after running sudo -i and hit **q** to exit manpages

Thanks.

I tried q and it did leave the manual, and I wish this foolish type of questions would not be required, perhaps if the documentation were clear about it.

Also, your reply

exit
q

was at first more cryptic than simple, but of course, effort is effort.

But thanks, anyway, dear Dude, and it does look to me that not everyone was in the light, as seen from other replies.

:)

---

### Post by gobuntu on 2007-10-28
Well,

I just tried  "logout" and it also "un-sudo'ed" me.

By the way, the documentation I have been studying says that "exit" is "exit the shell", and to me "exit the shell" meant "close the terminal", but not any more.

Thanks everyone.

---

