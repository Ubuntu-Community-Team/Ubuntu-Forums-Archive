---
title: "How do I add users but keep settings?"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by RKCole on 2007-04-18
Hello, everyone.

I was kind of curious about this topic as a question arose on the Ubuntu accessibility Mailing List.  When a uswer is added, what must one do to keep settings from another account?  For example, I have my magnifier configured for my username on Ubuntu.  If I was to create another user account, the configuration has to be re-created manually.  Is there some way which I can carry my settings over to other user accounts which I create?  If so, how can this be done in the terminal?

Thanks for any advice.

Take care.

---

### Post by aysiu on 2007-04-18
Let's say the first user is called Gemma and the second user is called Stuart: ```
sudo adduser stuart
sudo cp -R /home/gemma/* /home/stuart
sudo chown -R stuart:stuart /home/stuart
```

---

### Post by amohanty on 2007-04-18
> **aysiu said:**
> Let's say the first user is called Gemma and the second user is called Stuart: ```
sudo adduser stuart
sudo cp -R /home/gemma/* /home/stuart
sudo chown -R stuart:stuart /home/stuart
```

For the most part that works. However sometimes some pathological files may hang onto the username. Just to be on the safe side do a:

find | xargs grep old_username

That will give you a list of files that have old_username in it. You can manually modify those, or just blow them away.

Also keep in mind that some older versions of firefox and thunderbird recreate profiles which may lead to trouble.

HTH
AM

---

### Post by RKCole on 2007-04-18
Thanks, aysiu and amohanty.

I'm not sure if this has to do with the issue now...Let me explain some more in detail...

The user who posted on the mailing list uses Orca (a program which works with the Gnome magnifier, screen reader, and various other assistive technology software programs.  The user had asked how to create new user accounts, so I wrote back and mentioned to use:
```

sudo useradd <username>
sudo passwd <username>

```
as the user wanted to do this from the terminal.  He wrote back later on and informed me that the sound on the newly created user account did not work, so I thought that this had to do with settings from the old account not being carried over.  I'm not sure if I am correct in this assumption.

I seen a post while doing a Forum search whihc had somewhat of the same problem--a new user accoutn was created, but there was no sound.  The solution given for this ([link to post]("http://ubuntuforums.org/showthread.php?t=411661&highlight=adding+new+users")) was to add the user/group association for the audio group by
```

sudo addgroup <username> audio

```

Is this more of an issue with newly created users' rights?  And if so, what should one do to give a newly created user similar rights compared to the original account?

I apologize for my ignorance in this matter.  I'm still learning, step by step, and I hope to one day be able to call myself an "expert". :)

Thanks again for the help.

---

### Post by amohanty on 2007-04-18
AFAIK if you use useradd, the user is created and a group with the same name and setup appropriate files. Now to use a whole bunch of things, you need the user to be part of a whole lot of other groups. Just do a :

cat /etc/group | grep your_username 

to see how may of them you belong to. You can then use that as a template to modify the user or directly editing the group file and setting up the user appropriately, I would still advise using the GUI as its harder to screw up with that. 

HTH
AM

---

