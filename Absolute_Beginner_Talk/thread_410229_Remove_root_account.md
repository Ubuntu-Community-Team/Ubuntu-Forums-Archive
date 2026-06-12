---
title: "Remove root account"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by skm376 on 2007-04-15
I recently purchased a laptop that had Ubuntu (edgy eft) pre-installed.  This was all good with me cause I was planning to install Ubuntu anyway.  However, I am accustomed to using Ubuntu without a root account and there is a root account on my laptop.  I want to remove the root account so that the only account is mine and I can go back to 'sudo'ing everything.  Is there anyway I can remove the root user/account?  I have created my account on the system, but if I try to remove root I get an error that says: Administrator account cannot be deleted...this would leave the system unusable.

Any advice would help.

Thanks,

skm1126

---

### Post by N Clement on 2007-04-15
So are you able to use the command 'su' to switch to super user mode when you are in the terminal on your normal account?

---

### Post by zenwalker on 2007-04-15
With out a king, how would the dynasty or the kingdom run correctly and in a perfect way??

In the same way, Root is like a king of your system (Linux) so with out the root user, you cant operate your system coz every permission is given to root user.

Oh yea theres other way, you can set the GID and UID for your own custom user account same as the root accounts. So that youll have the same permissions and authorizations as the root has. 

**But its not secure!!!!**

---

### Post by skm376 on 2007-04-15
Yes.  I can su to root from my account.  And I don't want to be able to do this anymore.

---

### Post by Wim Sturkenboom on 2007-04-15
There is always a root account, but in Ubuntu it's 'disabled' by default. You can try *sudo password -l root* in a terminal to lock the account.

---

### Post by dest581 on 2007-04-15
You can use sudo with root still there.  If you're afraid of someone hacking, change root's password to something long and complex.  Otherwise, there's no reason to remove it.

---

### Post by ibanezix on 2007-04-15
Some people actually prefer to have a root account separately and enable the su thing. To disable it, have a look at these post in the Ubuntu Guide:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_disable_root_user_account](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_disable_root_user_account)

---

### Post by dbott67 on 2007-04-15
As mentioned earlier by Wim, root is disabled by default in Ubuntu (i.e. no one can login as root).  For more details on this please read:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

-Dave

---

### Post by TheWizzard on 2007-04-15
make sure you have sudo permissions before you disable the root account.

---

### Post by skm376 on 2007-04-15
Thanks for the replies.  I locked the root account using sudo passwd -l root.

---

