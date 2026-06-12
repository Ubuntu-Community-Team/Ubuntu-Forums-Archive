---
title: "updating program in /usr"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by Kuraboy on 2006-04-09
well... I got an advice to open a new thread for my question... thnx ^_^

> Hi.

I am new here...

I have a question regarding the root thing...

I am trying to instal subeclipse in eclipse... but it give me an error while trying to create a feature file... it means that I am not logged in as a root right?!

and I had the same problem while updating Azureus... it give me "permission denied" ... how can I type sudo and run these programs?! or can't I... must I log in as a root?!

*I dont know how to quote from another thread and put it here*

---

### Post by taurus on 2006-04-09
What do you mean by creating a feature file and upgrading azureus?  How did you install azureus in the first place?  Did you go thru Automatix or did you download and install it by hand?  If you want to install add-on to your eclipse, you need to be root unless you want to install it on your home directory.  How did you try to install the add-on or feature in eclipse anyway?

---

### Post by Kuraboy on 2006-04-09
thnx

I installed eclipse through synaptec and installed azureus through automatix.

I tryed to install subeclipse by going to help >> software update >> Find and Install [in eclipse]

then it gave me an error while creating files in /usr...

and Azureus give me : "ersion 2.0 of plugin 'azplugins' failed to install - /opt/azureus/plugins/azplugins/azplugins_2.0.jar (Permission denied)"

while installing updates... 

I managed to type sudo eclipse... and it seamed that I managed to install subeclipse.

but still I cant type sudo azureus. It cant find it.

thnx.

---

### Post by taurus on 2006-04-09
Then why don't you run azureus with the sudo command so it can write to /opt/azureus/plugins/azplugins/...
```

sudo azureus

```

---

### Post by Kuraboy on 2006-04-09
hi 

I cant. it tell me command not found :(

what can I do?

thnx

---

### Post by taurus on 2006-04-09
[QUOTE=Kuraboy]hi 

I cant. it tell me command not found :(

what can I do?

thnx[/QUOTE]
I suppose you installed azureus in /opt/azureus, right!  Then, run it like this
```

sudo /opt/azureus/azureus

```

---

### Post by Kuraboy on 2006-04-09
thank you very much for the fast reply...

it worked... thnx again ^_^

---

### Post by RLovelett on 2007-03-24
I get that the sudo command works as a root user and such.  But I have a shortcut inside of Applications -> Internet -> Azureus.  I want to be able to fully update whenever I click that link.  Is that at all possible?

---

### Post by taurus on 2007-03-24
> **RLovelett said:**
> I get that the sudo command works as a root user and such.  But I have a shortcut inside of Applications -> Internet -> Azureus.  I want to be able to fully update whenever I click that link.  Is that at all possible?

Yes, you just need to change the ownership of the directory where you installed azureus from root to your login name.  Then, you can write to it so you can update/uprade it.

Where did you install it and what is your login name?

---

### Post by RLovelett on 2007-03-24
Not quite sure where I installed it to. :(  I'm still new at this Linux thing.  But here is the tutorial I followed.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29)

---

