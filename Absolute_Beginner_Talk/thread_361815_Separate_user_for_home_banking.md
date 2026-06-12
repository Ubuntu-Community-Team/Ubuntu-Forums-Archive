---
title: "Separate user for home banking?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by hito1 on 2007-02-14
Here is the situation:

I first installed Ubuntu out of curiosity - I had never used an OS other than Windows - and used to boot into it very rarely, one good side effect of this is that my Ubuntu was a fairly 'virgin' environment, so I was confident enough to do on-line shopping and banking with it, wich I never did on the XP boot.

What happened is that I'm spending more and more time in Ubuntu, surfing the web, installing apps and so. It's not so 'virgin' anymore, and I fear that I'm not as safe as I was before. My question is:

1. If I create a separate user and use it only for on-line banking/shopping, will my surf behaviors and urges to try new programs endanger that safe login? Put in another way, can I relax with my normal login and still be safe (relatively, I know) with the bank/shopping user?

2. Going further with the question, should I create yet another user for those times when I'd like to ignore risks and just surf in a click frenzy and try everything new? A mess up user? (currently, I do that with the LiveCD, but it'd be nice if it could be done through a new login)

Thanks. :)

---

### Post by aysiu on 2007-02-14
Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

A virgin installation is no safer than one that has been used.

Also, even when you're the administrator of Ubuntu, you're usually a regular user. You become a superuser for only certain tasks and only for a limited time.

---

### Post by igknighted on 2007-02-14
> **hito1 said:**
> Here is the situation:

I first installed Ubuntu out of curiosity - I had never used an OS other than Windows - and used to boot into it very rarely, one good side effect of this is that my Ubuntu was a fairly 'virgin' environment, so I was confident enough to do on-line shopping and banking with it, wich I never did on the XP boot.

What happened is that I'm spending more and more time in Ubuntu, surfing the web, installing apps and so. It's not so 'virgin' anymore, and I fear that I'm not as safe as I was before. My question is:

1. If I create a separate user and use it only for on-line banking/shopping, will my surf behaviors and urges to try new programs endanger that safe login? Put in another way, can I relax with my normal login and still be safe (relatively, I know) with the bank/shopping user?

2. Going further with the question, should I create yet another user for those times when I'd like to ignore risks and just surf in a click frenzy and try everything new? A mess up user? (currently, I do that with the LiveCD, but it'd be nice if it could be done through a new login)

Thanks. :)

I don't see how a new user would be helpful for either, just be smart about erasing dangerous cookies and don't save your banking password/username in your browser.  Also, don't allow any program to run or package to install if you don't know what it is.

---

### Post by figgles on 2007-02-14
> **hito1 said:**
> Here is the situation:
1. If I create a separate user and use it only for on-line banking/shopping, will my surf behaviors and urges to try new programs endanger that safe login? Put in another way, can I relax with my normal login and still be safe (relatively, I know) with the bank/shopping user?

2. Going further with the question, should I create yet another user for those times when I'd like to ignore risks and just surf in a click frenzy and try everything new? A mess up user? (currently, I do that with the LiveCD, but it'd be nice if it could be done through a new login)

Thanks. :)I would never minimize security risks, but you're no longer in that center of a target that the Windows OS places you in. Having said that:

1) Disable Javascript except when you absolutely need it. "[No Script]("https://addons.mozilla.org/firefox/722/")" is a great firefox extension for this purpose -- your default behavior can disable it but you can enable it as needed.

2) I don't know what your surf behaviors are, but use the same rule as this: would the sites you visit reflect whether, in real life, you'd get your wallet back if you left it behind there? If you think "clicking like crazy" is safe, then it doesn't matter what OS you're on...

---

### Post by Talon2 on 2007-02-14
Interesting.

The last version of a Microsoft operating system I bought and used on a personal system was MS DOS 2.11.  As a result I've never had a virus or spyware and I have more change in my pockets.

I am not worried about doing what you want to do but if it makes you feel better certainly go forth and research the issue until you are confident that things are good to go.  You might limit your exposure by only working with one site until you are sure you are good to go.

---

### Post by aysiu on 2007-02-14
My bank doesn't allow me to save my username and password after I log out. I would hope no bank would...

---

### Post by hito1 on 2007-02-14
> **aysiu said:**
> 
Also, even when you're the administrator of Ubuntu, you're usually a regular user. You become a superuser for only certain tasks and only for a limited time.

I know that, what I want to know is if the mess-ups I eventually do with an user will spread to other users or not. Can we remove sudo privileges from an user?

---

### Post by aysiu on 2007-02-14
> **hito1 said:**
> I know that, what I want to know is if the mess-ups I eventually do with an user will spread to other users or not. Can we remove sudo privileges from an user?
Users, by default, cannot write to (i.e., change) other users files.

If you use the *sudo* command, you'll need authentication (password entry) every fifteen minutes. If the fifteen minutes thing is making you paranoid, you can change the *sudo* timeout to a shorter time (or no time):
[http://doc.gwos.org/index.php/Change_default_timeout_in_sudo](http://doc.gwos.org/index.php/Change_default_timeout_in_sudo)

---

### Post by hito1 on 2007-02-14
> **figgles said:**
> I would never minimize security risks, but you're no longer in that center of a target that the Windows OS places you in. Having said that:

1) Disable Javascript except when you absolutely need it. "[No Script]("https://addons.mozilla.org/firefox/722/")" is a great firefox extension for this purpose -- your default behavior can disable it but you can enable it as needed.

2) I don't know what your surf behaviors are, but use the same rule as this: would the sites you visit reflect whether, in real life, you'd get your wallet back if you left it behind there? If you think "clicking like crazy" is safe, then it doesn't matter what OS you're on...

Yeah, I've been using NoScript for a long time now. I don't even use Adblock, since NoScript already blocks the most annoying ads. :)

Of course I don't think "clicking like crazy" is safe, did you miss the point of the thread?

---

### Post by hito1 on 2007-02-14
> **aysiu said:**
> Users, by default, cannot write to (i.e., change) other users files.

If you use the *sudo* command, you'll need authentication (password entry) every fifteen minutes. If the fifteen minutes thing is making you paranoid, you can change the *sudo* timeout to a shorter time (or no time):
[http://doc.gwos.org/index.php/Change_default_timeout_in_sudo](http://doc.gwos.org/index.php/Change_default_timeout_in_sudo)
And can we strip sudo privilege from an user? Would this prevent spreading security risks to the others?

---

### Post by aysiu on 2007-02-14
> **hito1 said:**
> And can we strip sudo privilege from an user? Would this prevent spreading security risks to the others?
If there's a user you don't trust with *sudo*, you can definitely strip that user of *sudo* privileges.

The first user created during installation has *sudo* privileges, but when you create new users, you get the option to give them administrative privileges or not.

---

### Post by figgles on 2007-02-19
> **hito1 said:**
> Of course I don't think "clicking like crazy" is safe, did you miss the point of the thread?

No I didn't miss the point -- but for those moments of wild abandon, I would use a virtual environment, like VMWare, QEMU or VirtualPC (on Win/Mac). These let you set up a virginal OS, let you CLICK LIKE CRAZY (:-p) but then when you quit, you do not save your changes to the disk file that represents the environment. Thus, when you start again, you remain fresh and unaffected. Just be sure to not give local virtual drive access from the sandbox to your hard drive.

---

