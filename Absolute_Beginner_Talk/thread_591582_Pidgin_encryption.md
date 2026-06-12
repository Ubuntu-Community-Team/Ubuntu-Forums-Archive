---
title: "Pidgin encryption"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2007-10-25
I'd really like to install Pidgin-Encryption, the official site says it's in the repositories as "Gaim-Encryption" - but it's not. And it's not under pidgin-encryption, either. Any ideas? Thanks.

---

### Post by flossgeek on 2007-10-25
I'm running Gutsy and I see it in Synaptic. 

"pidgin-encryption"

---

### Post by atomkarinca on 2007-10-25
it should be "pidgin-encryption" not "Pidgin-Encryption" [http://packages.ubuntu.com/cgi-bin/search_packages.pl?sourceid=mozilla-search&searchon=names&keywords=pidgin-encryption&version=gutsy&subword=1&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?sourceid=mozilla-search&searchon=names&keywords=pidgin-encryption&version=gutsy&subword=1&release=all)

---

### Post by michaelzap on 2007-10-25
Personally I prefer the Off The Record plugin for Pidgin, so you might want to investigate that.

---

### Post by chimerical_brio on 2007-10-25
Ah, thanks a lot. I apt-cache searched and just didn't see it. What's the difference between OTR and pidgin-encryption?

---

### Post by n3tfury on 2007-10-25
i'd like to know the technical differences too.  i just installed pidgin-encryption.  unfortunately, nobody that's only currently on my buddylist uses pidgin :/

---

### Post by michaelzap on 2007-10-25
OTR works with Adium and Trillian, as well as Pidgin (Linux/Windows).

As far as the differences between OTR and pidgin-encryption, the OTR site says the following:

> How is this different from the pidgin-encryption plugin?
The pidgin-encryption plugin provides encryption and authentication, but not deniability or perfect forward secrecy. If an attacker or a virus gets access to your machine, all of your past pidgin-encryption conversations are retroactively compromised. Further, since all of the messages are digitally signed, there is difficult-to-deny proof that you said what you did: not what we want for a supposedly private conversation!

I've had OTR recommended to me by several people, and it's always worked for me across various IM clients and operating systems, so I like it.

More info here:
[http://en.wikipedia.org/wiki/Off-the-Record_Messaging](http://en.wikipedia.org/wiki/Off-the-Record_Messaging)

---

### Post by n3tfury on 2007-10-25
interesting.  guess i'll need to read up on how to install this plugin the old school way.  thanks for the information.

---

### Post by n3tfury on 2007-10-25
found some awesome instructions on these boards by kevdog

[http://ubuntuforums.org/showthread.php?t=558197](http://ubuntuforums.org/showthread.php?t=558197)

---

### Post by michaelzap on 2007-10-25
> **n3tfury said:**
> interesting.  guess i'll need to read up on how to install this plugin the old school way.  thanks for the information.

If you're using Gutsy, you can install it via Synaptic (search for pidgin-otr).

---

### Post by n3tfury on 2007-10-25
even better, thank you!  apt-get install pidgin-otr did the trick thanks!

---

### Post by jbang on 2007-10-25
> **michaelzap said:**
> Personally I prefer the Off The Record plugin for Pidgin, so you might want to investigate that.

I was wondering: Have any of you tried having both installed (OTR and pidgin-encryption)? Would that be possible? And would it then be possible to select encryption method on a per-buddy basis?

-- Jens

---

### Post by n3tfury on 2007-10-25
> **jbang said:**
> I was wondering: Have any of you tried having both installed (OTR and pidgin-encryption)? Would that be possible? And would it then be possible to select encryption method on a per-buddy basis?

-- Jens

check your private messages

---

### Post by Orbital75 on 2007-10-25
I used to use AIM encryption back in the day before I started using Pidgin.
With Aim encryption you could still talk to others that didn't have encryption   
but you wouldn't be encrypted. Yes, it defeated the purpose but still worked 
if the other person didn't have encryption implemented.  Can Pidgin encryption 
be enabled and still be able to chat with others that don't have encryption?

---

### Post by genbuntu on 2007-10-25
found this thread interesting... :)
I had the same question: Can we use Pidgin-encryption or pidgin-OTR with other buddies who use msn, yahoo mssngr etc and don't have encryption installed? Will encryption work?

---

### Post by n3tfury on 2007-10-25
no it won't work that way.

---

### Post by Orbital75 on 2007-10-25
Well, will Pidgin still message other clients?  I understand the encryption will be bypassed because
the other person isn't using the encryption. 

By the way.... I have 7.04 and when using the synaptic package manager only
Gain encryption and Gaim OTR comes up.  I installed them but I don't see the
option available in Pidgin.  I thought they may work since pidgin use to be Gaim.
How can I get them to come up and install for 7.04?

---

### Post by genbuntu on 2007-10-25
> **Orbital75 said:**
> Well, will Pidgin still message other clients?  I understand the encryption will be bypassed because
the other person isn't using the encryption. 



That's what I thought as well.
 I still have gaim under my applications menu even though I use pidgin (i.e. to say it exists independently of pidgin) , probably because it is still supported differently. So thats why installing gaim-otr etc won't show up in pidgin.

As mentioned before see this link for installation (through terminal of course ):
[http://ubuntuforums.org/showthread.php?t=558197](http://ubuntuforums.org/showthread.php?t=558197)

---

### Post by Orbital75 on 2007-10-26
I'm strongly considering install Pidgin encryption or OTR.  I'd really like to have someones
experience with connecting to non encrypted users.  Is it possible but without the
encrypted connection.  I just want to make sure I'll see be able to speak to buddies on
my list encrypted or not.

---

### Post by michaelzap on 2007-10-26
> **Orbital75 said:**
> I'm strongly considering install Pidgin encryption or OTR.  I'd really like to have someones
experience with connecting to non encrypted users.  Is it possible but without the
encrypted connection.  I just want to make sure I'll see be able to speak to buddies on
my list encrypted or not.

OTR only kicks in when both users have it, and when they don't it doesn't affect your communication at all. You can still talk to other contacts who don't use OTR, but the conversations will not be encrypted. You can even choose not to use OTR when both parties have it if you wanted to do that for some reason.

It's just a Pidgin plugin, so I recommend that you try it out. If you don't like it, you can just disable it in the plugin preferences. But if you want solid chat encryption, OTR is the way to go.

---

### Post by suchawato on 2007-12-03
LOL
You guys are makig this really difficult. :D
So,
Just right click on the pidgin icon on your task bar when it is running.
You'll see a little plugins icon.
click that, and a little menu comes up with all the avalible plugins.
that's it.
easy.
LOL
Realy, linux has gotten a lot easier than having to use the command line or synaptic for everything!
Pidgin does it for you!
See Ya!
LOL :D

---

### Post by michaelzap on 2007-12-03
> **suchawato said:**
> LOL
You guys are makig this really difficult. :D


It was more difficult in Feisty (since Pidgin wasn't in the repos, OTR hadn't been updated to work with it yet, and somethings wanted to install as Gaim), but it is as simple as you say now.

---

