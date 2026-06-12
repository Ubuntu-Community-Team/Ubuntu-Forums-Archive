---
title: "Hide Private IP???"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by richie82 on 2007-02-01
Hello all

I have been using ubuntu for the past month as a complete newbie to the linux scene.

I have firestarter, tor, and privoxy running yet the following website is still able to show on its java applet test that my ip is still discoverable. :-s I am concerned about this highly as my firewall test shows that all my ports are closed, and i thought linux was more of less completely free of malware, spyware etc...

i even have the torbutton plugin on firefox 2.0???

can someone help me with a simply and clear way of being able to hide my ip totally without impairing my internet experience.

thank you

---

### Post by DaveArb on 2007-02-01
You can't hide the address that you connect to the internet with. When you request a page from a web site, for example, it has to have your address in order to return the page.

By closing ports to incoming connections, you've "secured" your computer. If I, a bad guy, have your address but nothing will accept a connection, I pretty much have to move on somewhere else to do any damage.

A real world analogy is that you cannot hide your street address to avoid burglars. You wouldn't be able to get mail, get emergency services, or tell a friend how to stop by. What you to to help thwart the burglars is lock your doors and windows.

When you read about vulnerabilities, that's an example of the burglar tossing a brick through the window or picking the lock on the door. The updates are installing tougher glass, better locks... Sorry for straining an analogy. ;)

---

### Post by glabouni on 2007-02-01
sorry dave, although you are not wrong in what you said, it seems you missed something here: richie82 is using [tor]("http://tor.eff.org/"). The whole point of using tor is to avoid discolusre of your IP address while surfing the web.

anyways what is the following website you're mentioning ?

have you checked tor is up and running ?
you can follow this wiki entry to do so: [How can I tell if Tor is working, and that my connections really are anonymized? Are there external servers that will test my connection?]("http://wiki.noreply.org/noreply/TheOnionRouter/TorFAQ#head-0e1cc2ac330ede8c6ad1ac0d0db0ac163b0e6143")

---

### Post by mips on 2007-02-01
Kill Java and it will not happen.

---

### Post by DaveArb on 2007-02-01
> **glabouni said:**
> richie82 is using [tor]("http://tor.eff.org/"). The whole point of using tor is to avoid discolusre of your IP address while surfing the web.

Thanks for the info, I admit not know `tor` from the hole in my head. ;)

From a network point of view, I can't begin to imagine how that would work, guess I'll take a glance at it when I have a moment. Thanks again.

---

### Post by psyne on 2007-02-01
TOR uses a concept called onion routing. Imagine if you will a friend gives you letter to mail for him you place it in envelope and mail it to another friend who places the letter in a new envelope and mails it; on and on the letter is remailed and mailed till it gets to final destination. If it is intercepted along the way it is much more difficult if not pseudo impossible to track back through all the points where the original letter was mailed from.

As to the use of tor with Firefox I would suggest you take a look at torpark it is a fully enclosed tor system. It is for Windows only but works with wine. I installed it using Crossover office but from the torrify forums they say you can install it using wine alone.

[http://www.torrify.com/forum/viewtopic.php?t=124&sid=67be140937f08a59652a6010a814ee](http://www.torrify.com/forum/viewtopic.php?t=124&sid=67be140937f08a59652a6010a814ee)

As to your IP address if you have Java installed and running then it is still possible to figure out your IP address.

---

### Post by DaveArb on 2007-02-01
Ah, it's an anonymizer network! Thanks a ton, psyne, that was an excellent description.

I'm a corporate admin, first one of my users asks for that is going to faint from the dirty look they get... ;)

---

### Post by glabouni on 2007-02-01
> **DaveArb said:**
> Thanks for the info, I admit not know `tor` from the hole in my head. ;)

From a network point of view, I can't begin to imagine how that would work, guess I'll take a glance at it when I have a moment. Thanks again.

basically it an encrypted distributed network. each node only knows the previous node and the one that come after so there's no way to retrace the whole path from a node. 

when a packet is sent, the route is randomly selected, it is encrypted and transferred from node to node till it reaches the final node who delivers the packet to destination and then encrypt and send back the answer the way it came.

for further information have a look at this page: [How tor works]("http://tor.eff.org/overview.html.en").

---

