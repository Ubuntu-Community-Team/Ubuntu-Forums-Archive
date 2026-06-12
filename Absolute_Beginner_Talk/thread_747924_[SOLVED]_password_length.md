---
title: "[SOLVED] password length"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by hashi856 on 2008-04-07
Is there any way at all to have a user password length of less than 6 characters?

---

### Post by Michael.Godawski on 2008-04-07
> Is there any way at all to have a user password length of less than 6 characters?

If you mean the liogin password and the password you type in for getting superuser rights (sudo) then yes it is possible. If you use your machine in public places then it is not so recommend to have such a short password, but for home only usage, why not.

---

### Post by Crafty Kisses on 2008-04-07
As stated above, I wouldn't recommend such a short password, I'd make it at least 6 characters, anything shorter than that is asking to get figured out.

---

### Post by tommcd on 2008-04-07
Yes, you should be able to. Why do you ask? Are you having trouble setting up a password with less than 6 characters?
In general, a good password should be at least 5-6 characters, have both uppercase and lowercase letters,  numbers, and even some symbols. e.g.:
z3D6#m
Complex passwords can save your system from being hacked. Learn to love them. Security and convenience always compete. You can't have absolute convenience and absolute security at the same time.

---

### Post by mjp216 on 2008-04-07
why would you want to?

---

### Post by gordintoronto on 2008-04-07
It's my system, I should be able to do what I want with it.  That includes having my choice of password.  I find the requirement for a complex password intrusive.

Two people said, yes, you can have a short password, but they did not say how to do it!

---

### Post by bodhi.zazen on 2008-04-07
> **gordintoronto said:**
> It's my system, I should be able to do what I want with it.  That includes having my choice of password.  I find the requirement for a complex password intrusive.

Two people said, yes, you can have a short password, but they did not say how to do it!

In general, if you are wanting to circumvent security features you are expected to read and figure it out on your own. This is the one area where most of the staff take a "RTFM" policy. If you want to do this google is your friend.

---

### Post by hashi856 on 2008-04-09
Funny, I thought forums were for helping people, not telling them to figure it out on there own. It's my computer, no one uses it but me, Why do you have a problem with it? I hate it when I find things that are easier to do on windows than linux.

---

### Post by Tatty on 2008-04-09
> **hashi856 said:**
> Funny, I thought forums were for helping people, not telling them to figure it out on there own. It's my computer, no one uses it but me, Why do you have a problem with it? I hate it when I find things that are easier to do on windows than linux.

I understand your frustration, however, doing things such as having insecure passwords (such as less than 6 characters), or disabling passwords altogether are very dangerous things to do on any computer system.

Giving out the information on how to do this without simultaneously giving out enough information to explain why you shouldn't do it is a recipe for disaster...

The idea is that if you know enough about what you are doing to make an informed decision about something like this, then you will also know enough to do it.  Or at least enough to know how to find out how to do it.

[This article]("https://help.ubuntu.com/community/RootSudo?highlight=%28rootsudo%29") is an essential read as to why not do compromise your passwords in this way, and you should at the very least read this fully before you decide if you want to make such a significant change to your system security.

---

### Post by hashi856 on 2008-04-09
Ok well I found the solution (no thanks to Ubuntu community). It's actually really simple. 

Open a terminal,

type "sudo -i"
type in password if prompted

enter "passwd username" replace "username" with the user name of the account whose password you are trying to change

it will ask you for a new unix password. 

Type what ever you want.

Bam, you got a new password of what ever length you want.

---

### Post by conscious on 2008-04-09
Or, in just one step: ```
sudo passwd *username*
```

---

### Post by Tatty on 2008-04-09
> **conscious said:**
> Or, in just one step: ```
sudo passwd *username*
```

This is much safer too, logging in as a persistant superuser is not good practice, as it is too easy to forget to log out again and you could easily do your system some damage without meaning to.

But once again, just for the record... Having a password less than 6 characters long is unsafe as it could easily bee cracked or guessed.  But ultimately it is your system you are risking so it is your choice.

---

### Post by jakupl on 2008-04-09
Please mark thread at solved, to save time for us all.

---

### Post by bodhi.zazen on 2008-04-09
> **hashi856 said:**
> Funny, I thought forums were for helping people, not telling them to figure it out on there own. It's my computer, no one uses it but me, Why do you have a problem with it? I hate it when I find things that are easier to do on windows than linux.

Not where security is involved. The overwhelming consensus of the staff is that if you want to circumvent security you should be prepared to RTFM and understand what you are doing. It is in our opinion for your own protection.

We even have policies on such things (although logging in as root is not exactly the same, it is the same vein, IMO at least):

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

You are of course free to run your box the way you wish and we are here to help with technical questions, just not circumvention of security.

---

### Post by JBA2337 on 2008-04-11
When I first installed Ubuntu I entered a one-letter password for everything: login password, wireless keyring password, and sudo password. I guess some people would call this foolhardy and stupidly risky, but I am the only person who ever has or ever will use this computer. The computer stays in one place all the time (my home), and will never leave. I am connected to the Internet through a wireless connection, which has a 10-character random password. 

So far, no problems caused by lax security have been observed. I have only been using Ubuntu now for about 4 weeks.

Any comments about security and passwords would be appreciated.

JBA2337

---

### Post by bodhi.zazen on 2008-04-11
> **JBA2337 said:**
> When I first installed Ubuntu I entered a one-letter password for everything: login password, wireless keyring password, and sudo password. I guess some people would call this foolhardy and stupidly risky, but I am the only person who ever has or ever will use this computer. The computer stays in one place all the time (my home), and will never leave. I am connected to the Internet through a wireless connection, which has a 10-character random password. 

So far, no problems caused by lax security have been observed. I have only been using Ubuntu now for about 4 weeks.

Any comments about security and passwords would be appreciated.

JBA2337

The sad reality is that unless you are disconnected from the internet you are not the only person with access to your computer.

Even Microsoft has come to realize this as their boxes are turned into botnet zombies by the thousands.

[http://www.microsoft.com/protect/yourself/password/create.mspx](http://www.microsoft.com/protect/yourself/password/create.mspx)

[http://www.microsoft.com/protect/yourself/password/checker.mspx](http://www.microsoft.com/protect/yourself/password/checker.mspx)

---

### Post by JBA2337 on 2008-04-11
To: bodhi.zazen

Thanks, After I read your post I immediately changed all my passwords to 10 characters, with a random sequence of numbers and letters. I did not realize that these passwords are protecting me from evildoers on the Internet. I was not sure exactly who I need to protect myself from.

If you could, please elaborate some more as to why we need to use difficult passwords.  Your comments are greatly appreciated.

JBA2337

---

### Post by bodhi.zazen on 2008-04-11
[Who Are These Crackers, Anyways?](http://home.actlab.utexas.edu/~aviva/compsec/cracker/whocrack.html)

---

### Post by tpscan on 2008-04-20
FWIW -- the password policy documents are not readily accessible or intelligible to everyone. 
It is possible to point to a specific manual section, without revealing the secrets of the sanctum.

 **RTFM** -- is often very unhelpful,  as the Linux admin manual is quite large. 
A simple  posting of this line: ***>$ man -k password***
or  ***>$ man -k pam***
does not compromise security, but might lead someone to a more general solution.

I ended up reading this thread because I was trying to relax the general password validation rules. Not set a password, once.

Again this is a single machine, in a secure location, used by two people.
I was setting up an account for a non-computer using spouse,
who needed to research health issues. My spouse has lost a lung to cancer.
Meds and health compromise her eyesight and her dexterity.
Typing long or complex passwords are not possible.
Making it possible for her to pick a reasonable and memorable password is better than none.
Her account would be restricted in any case, 
but long, mixed case, alpha-numeric passwords would simply bar her from use.

Of course, I could just give her a Windows machine, 
since maintaining security on Linux is such an issue?  
My $0.02 is that there are cases where folks need to configure system policy, 
without needing to know all the details of etc/pam.config. 
 
And Google *"Linux password configuration policy"* 
or "password validation rules" or" PAM configuration"
and variants like that don't really lead to results that are helpful.
In my mind, these fora should be the first place to look.
Forget the manual, just check the source!

---

### Post by bmac on 2008-04-20
I think there may be a big misunderstanding here. One - the security issue of a password, two - the concept that the forum family is not responsive.   I'll like to address number one first: As the individual indicated it's his machine, preaching anything in a deeming tone usually results in attitude... Might I suggest we ask to assist individuals with similar issues outside the forum (e-mail). As he indicated this was his machine and his choice!!! I do understand the forums reluctance to respond, especially when it could be viewed and attempted by a different individual - with devastating results.  Two: The concept that this forum is anything but responsive because individuals in the forum have elected not to assist in the potential demise of the Ubuntu experience, is foolish. However, it may appear to a newbie that this is exactly what happened in this case. I'm not questioning the responses to the thread, just how we react to an individual that is directly requesting support for their own machine. Few of us have all the answers (in my case very few answers) but together we are capable of solving problems through direct interaction. When we choose to react in a condescending manner it can truly impact the individual and make the experience unpleasant.   Just my opinion - I could be wrong...

---

