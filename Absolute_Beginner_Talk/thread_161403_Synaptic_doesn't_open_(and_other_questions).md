---
title: "Synaptic doesn't open (and other questions)"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by Hiroshima on 2006-04-17
This is my first post, and my first full day with linux. (Ubuntu)

I had some trouble installing, the usuall freeze was on "copying packages to hard disk".  After several attempts, I tried installing without ACPI (?) disabled.  I also forgot to take the CD out of the drive at re-boot, however, it seemed to finish the job as the login screen was waiting for me when I came back to the computer.

I installed on a new partition so that I can still use Windows until I get Ubuntu configured and learn what I'm doing.

To start, I want to install Japanese Language support (I saw the instructions on the wiki) but I cannot open synaptic.  I put in my password (Question 1, I am supposed to use my user password here right?) and then nothing happens.  I can hear the hard drive start for a second, then nothing. (Question 2 What should I do?)

I also want to install mozilla thunderbird - (Question 3) Is that through synaptic as well?

Thanks for any help,  Hiroshima

---

### Post by unbuntu on 2006-04-17
[QUOTE=Hiroshima]This is my first post, and my first full day with linux. (Ubuntu)

I had some trouble installing, the usuall freeze was on "copying packages to hard disk".  After several attempts, I tried installing without ACPI (?) disabled.  I also forgot to take the CD out of the drive at re-boot, however, it seemed to finish the job as the login screen was waiting for me when I came back to the computer.

I installed on a new partition so that I can still use Windows until I get Ubuntu configured and learn what I'm doing.

To start, I want to install Japanese Language support (I saw the instructions on the wiki) but I cannot open synaptic.  I put in my password (Question 1, I am supposed to use my user password here right?) and then nothing happens.  I can hear the hard drive start for a second, then nothing. (Question 2 What should I do?)

I also want to install mozilla thunderbird - (Question 3) Is that through synaptic as well?

Thanks for any help,  Hiroshima[/QUOTE]

Hello,

It happens to me before.
Probably you need to add this line to your /etc/sudoers file:
```

your_login_name   ALL=(ALL) ALL

```

Make sure you edit this file using visudo command, and also make sure you have the root privilege.

EDIT: typo corrected

---

### Post by Hiroshima on 2006-04-17
Wow, that was very fast, thank you!

However, I don't understand .. how do I add something to the sudoers file?

{Probably you need to add this line to your /etc/sudoers file:
Code:

your_login_name ALL=(ALL) ALL}

Thanks,  Hiroshima

---

### Post by unbuntu on 2006-04-17
Go to terminal, type command "sudo visudo" and an editor screen will show up (after you typed in the root password of course)

Then you just add the line at the bottom of the file, save it as the original name (/etc/sudoers), and you're done.

---

### Post by Hiroshima on 2006-04-17
Sorry to be such a nuicance, how do I go to terminal.  I looked all through Applications Places and System, and couldn't find anything that looked right.

---

### Post by wat3r on 2006-04-17
I don't have an english version of Ubuntu, but it is located under Programs -> Accessories (?) - Terminal.
But I think you will have to boot into recovery mode to edit sudoers.

---

### Post by Hiroshima on 2006-04-17
You were right, Applications>accessories>terminal.  I did look there, sorry.

---

### Post by localzuk on 2006-04-17
The problem with this advice is that in order to edit the sudoers file you need to be in the sudoers file already...

If you are not in the sudoers file, you need to restart the computer and press escape when the grub loader shows. Choose the failsafe option. 

You will eventually come to a prompt allowing you to execute commands.
From this prompt, you should enter ```
nano /etc/sudoers
```

In this window, scroll through the file using the arrow keys. If  you do not come across a line like that mentioned above then add one.

Save the file (ctrl + x, followed by y and enter). Now type 'reboot'. Boot back in to normal ubuntu and try Synaptic again.

---

### Post by unbuntu on 2006-04-17
[QUOTE=localzuk]The problem with this advice is that in order to edit the sudoers file you need to be in the sudoers file already...

If you are not in the sudoers file, you need to restart the computer and press escape when the grub loader shows. Choose the failsafe option. 

You will eventually come to a prompt allowing you to execute commands.
From this prompt, you should enter ```
nano /etc/sudoers
```

In this window, scroll through the file using the arrow keys. If  you do not come across a line like that mentioned above then add one.

Save the file (ctrl + x, followed by y and enter). Now type 'reboot'. Boot back in to normal ubuntu and try Synaptic again.[/QUOTE]

Actually, more likely he did an expert installation, and has the root account activated already, so he can su to root account and visudo.

---

### Post by Hiroshima on 2006-04-17
Once again, thanks for all the advice.  Last night, I tried going to terminal,
 I saw my user name, and typed:
[COLOR="DarkOrange"]sudo visudo[/COLOR]
Then I entered my password at the prompt
then I saw my user name again... I think I should have been looking at a script to edit at that point.  I tried entering 
[COLOR="DarkOrange"]your_login_name   ALL=(ALL) ALL[/COLOR]
and   [COLOR="DarkOrange"]ALL=(ALL) ALL[/COLOR]

assuming that there is no script there to edit or to add a line to, did I do the right thing?

also, [COLOR="DarkOrange"]your_login_name [/COLOR] should I replace that with (for example) hiroshima ALL=(ALL) ALL, or should it be entered just as is?

I'm not sure if I did an expert installation or not.

I will try this again when I get home tonight, as well as **local zuk's ** advice. I will also try anything else that is suggested in the meantime.

Thanks again for the ideas,

Hiroshima

---

### Post by unbuntu on 2006-04-17
[QUOTE=Hiroshima]Once again, thanks for all the advice.  Last night, I tried going to terminal,
 I saw my user name, and typed:
[COLOR="DarkOrange"]sudo visudo[/COLOR]
Then I entered my password at the prompt
then I saw my user name again... 
[/QUOTE]
You mean you didn't see the editor screen popped up?  Then maybe they are right, you should do it under recovery mode.


> 
I think I should have been looking at a script to edit at that point.  I tried entering 
[COLOR="DarkOrange"]your_login_name   ALL=(ALL) ALL[/COLOR]
and   [COLOR="DarkOrange"]ALL=(ALL) ALL[/COLOR]

assuming that there is no script there to edit or to add a line to, did I do the right thing?

Not sure what you mean by "no script there to edit or add a line to".  But if everything is done right, after "visudo", you should get a editor screen loaded with /etc/sudoers, and you can then modify it.

> 
also, [COLOR="DarkOrange"]your_login_name [/COLOR] should I replace that with (for example) hiroshima ALL=(ALL) ALL, or should it be entered just as is?

I'm not sure if I did an expert installation or not.

I will try this again when I get home tonight, as well as **local zuk's ** advice. I will also try anything else that is suggested in the meantime.

Thanks again for the ideas,

Hiroshima

Yes.  Replace your_login_name with your actual login name.

---

### Post by Hiroshima on 2006-04-18
That's right, assuming the editor screen and the place I typed my password are different, then no editor screen popped up.

I will try in recovery mode when I get home.

Hiroshima

---

### Post by Hiroshima on 2006-04-18
Ok, here we go... this is the live version.

started in failsafe (recovery)

typed [COLOR="Red"]nano /etc/sudoers[/COLOR]
entered my root password
 it opened two blank files, "etc" and "sudoers"
then I typed... darn, what did i put in... nano[COLOR="Red"][/COLOR] maybe,

now i see the file /etc/sudoers.tmp  there is a line
[COLOR="Lime"]root ALL=(ALL)  ALL[/COLOR]
changing it to 
[COLOR="Red"] my_user_name ALL= (ALL) ([/COLOR]

Save the file (ctrl + x, followed by y and enter). Now type 'reboot'. Boot back in to normal ubuntu and try Synaptic again.

ubuntu started ok, logged in... and 

Synaptic is open.

Thank you everyone.  I may be back soon with another thread if I can't figgure something else out, but there is no way I could have done this without all your suggestions.  

Thank you,

Hiroshima.

---

### Post by unbuntu on 2006-04-18
[QUOTE=Hiroshima]Ok, here we go... this is the live version.

now i see the file /etc/sudoers.tmp  there is a line
[COLOR="Lime"]root ALL=(ALL)  ALL[/COLOR]
changing it to 
[COLOR="Red"] my_user_name ALL= (ALL) ([/COLOR]
[/QUOTE]

Just add that line should suffice.  No need to replace the root line.  In the future, you may want to enable the root account, in which case you'd be in trouble because you don't have that line.

---

### Post by gardara on 2006-04-18
I had the same problem and was able to fix ths problem with visudo, thanks for the instructions :)

btw. maby this should be written in the wiki? ;)

---

