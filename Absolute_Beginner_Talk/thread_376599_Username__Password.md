---
title: "Username / Password"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by loanrangie on 2007-03-05
I have just installed Ubuntu as a dual boot with XP till i get my head around it but when i try to log in (after booting) i entered my username which i think is the name i gave my pc and the password i chose but am unable to login. Is it possible to bypass the login so i can fix it or remove it altogether - i really dont need/ want to have to login each time.

thanks,
nick.

---

### Post by jamyskis on 2007-03-05
> **loanrangie said:**
> I have just installed Ubuntu as a dual boot with XP till i get my head around it but when i try to log in (after booting) i entered my username which i think is the name i gave my pc and the password i chose but am unable to login. Is it possible to bypass the login so i can fix it or remove it altogether - i really dont need/ want to have to login each time.

thanks,
nick.

You can log in through recovery mode (from GRUB) and type cat /etc/passwd. This will give a list of all available users, you should be able to find your user name in there somewhere. If you've forgotten your password (attention to capitalisation) then you have a problem. You can always add a new user in recovery mode and add it to the various admin groups.

---

### Post by loanrangie on 2007-03-05
> **jamyskis said:**
> You can log in through recovery mode (from GRUB) and type cat /etc/passwd. This will give a list of all available users, you should be able to find your user name in there somewhere. If you've forgotten your password (attention to capitalisation) then you have a problem. You can always add a new user in recovery mode and add it to the various admin groups.

 Thanks mate, i will give it a go.

---

### Post by loanrangie on 2007-03-05
Ok, i booted into recovery mode and when it finished loading i get  ' root@ubuntunicks' and a prompt , so where do i go from here ?

---

### Post by pandu.rs on 2007-03-05
once u r in the recovery mode type the following command

cat /etc/passwd | grep 1000 | cut -d: -f1

this will print the username (first user that u created)

if u have forget the password, u can reset the passwd using the following command

passwd <username>

---

### Post by jamyskis on 2007-03-05
OK, forget this post - pandu.rs' suggestion is far better :mrgreen:

---

### Post by loanrangie on 2007-03-05
> **pandu.rs said:**
> once u r in the recovery mode type the following command

cat /etc/passwd | grep 1000 | cut -d: -f1

this will print the username (first user that u created)

if u have forget the password, u can reset the passwd using the following command

passwd <username>

 After root@ubuntunicks i get a # then a prompt, i tried typing the above but just get ' no file or directory found' ? Also the 2  letters or such either side og grep 1000, what are they ? capitol i's ? I know in Windows you usually get a prompt like c: etc but this is my first Linux install so it all looks greek to me.

---

### Post by konst88 on 2007-03-05
It is not I, it is | , shift+backslash.

---

### Post by pandu.rs on 2007-03-05
> **loanrangie said:**
>  Also the 2  letters or such either side og grep 1000, what are they ? capitol i's 

That's pipe symbol (used a OR symbol in many languages including C)
You can find this above or below the enter key or before the backspace key

If you are still getting 'file not found' then paste the output of the following commands here

mount
fdisk -l  (l as in ell)

---

### Post by loanrangie on 2007-03-05
> **pandu.rs said:**
> once u r in the recovery mode type the following command

cat /etc/passwd | grep 1000 | cut -d: -f1

this will print the username (first user that u created)

if u have forget the password, u can reset the passwd using the following command

passwd <username>

 Tried this numerous times but still get 'file or directory not found', when i load in recovery mode at the end i get ' root@ubuntunicks ~# (nicks is my pc name for network) and then a cursor on the next line ? the ~ symbol is actually higher than the # if it makes any difference. Also how do i copy and paste the outcome here ? I have to restart and then boot into XP each time i need web access ?

---

### Post by pandu.rs on 2007-03-05
> **loanrangie said:**
> the ~ symbol is actually higher than the # if it makes any difference.

This does not make any difference.

> **loanrangie said:**
> Also how do i copy and paste the outcome here ? I have to restart and then boot into XP each time i need web access ?

Since u r in recovery mode console, u cannot copy paste, as you used to do in normal mode
Yes, you need to boot into any other OS each time you need web access unless you have another machine.

i booted my machine into recovery mode and checked this command. It is working fine for me.

Probably you can reinstall ubuntu (I hope you have just installed it) and this time remember the username :)

---

### Post by loanrangie on 2007-03-05
> **pandu.rs said:**
> This does not make any difference.



Since u r in recovery mode console, u cannot copy paste, as you used to do in normal mode
Yes, you need to boot into any other OS each time you need web access unless you have another machine.

i booted my machine into recovery mode and checked this command. It is working fine for me.

Probably you can reinstall ubuntu (I hope you have just installed it) and this time remember the username :)

 I think a reinstall will be the easiest fix, the bit about web access shouldnt have had the question mark as that was a no brainer - thanks for helping with my noobie questions.

nick.

---

### Post by loanrangie on 2007-03-06
Finally up and running with Ubuntu, had to re install after deleting partitions , no wonder i couldnt remember my username as i wasnt asked for one , during install you are given óem'and &#347;udo ´as usernames to login . Now i have it sorted its time to explore this OS and see if i can live with it fulltime.

---

### Post by pandu.rs on 2007-03-06
Just in case u did not know this
u can enable automatic login as follows

go to 
system->administration->login window->securiy

check 'Enable automatic login' and choose the user. 

Bingo. Next time ur system should login automatically!

---

