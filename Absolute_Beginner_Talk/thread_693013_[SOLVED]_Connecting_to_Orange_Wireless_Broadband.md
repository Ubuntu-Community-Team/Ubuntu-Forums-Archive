---
title: "[SOLVED] Connecting to Orange Wireless Broadband"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Beaker Boy on 2008-02-10
Hi there!  As a newbie, I am struggling to connect my LINUX laptop to my Orange Wireless Router.  I'm running Gutsy, and have been able to connect other home wireless broadband routers.  I'd be grateful if anyone had any prompts that would set me in the right direction.

Many thanks

---

### Post by ugm6hr on 2008-02-10
To clarify:
Your wifi definitely works on Gutsy
Your internet works with Orange

The problem is you can't connect to the Orange router...

What encryption do you use?
Do you use MAC filtering?
Do you dual-boot?  If so - does the laptop connect in Windows?
Can you connect with ethernet cable?
Do you hide your wifi SSID?
Can you "see" your wifi SSID listed in Network Manager?

Just some useful info to point us in the right direction.

---

### Post by Beaker Boy on 2008-02-11
Many thanks for getting back to me so quickly.  In answer

I'mm currently using the default WEP encryption although have asked Orange to send me details on upgrading to WPA.

I don't think I'm using MAC filtering but I'm not sure as I don't know what it is.

I'm not using dual boot

I haven't tried the ethernet cable yet but will give it a go later

I'm afraid I don't know what you mean by 'Do you hide your Wifi SSID'

I can definetly see my Livebox when I click on the dual-computer logo in the top right hand corner of the screen. It only lets me chose WPA and LEAP(?) options.

I know there are some issues with the Livebox and connecting to Ubuntu.  I know the computer and Ubuntu aren't the problem as I used my Mum's wireless router (a Voyager connected to Waitrose as the ISP) so it's all in the Livebox.  As an aside do you know if there is a way of using a different router to get to Orange if this problem is intractable?

Many thanks for your help so far

Beaker Boy

---

### Post by ugm6hr on 2008-02-11
> **Beaker Boy said:**
> I'mm currently using the default WEP encryption although have asked Orange to send me details on upgrading to WPA.

I don't think I'm using MAC filtering but I'm not sure as I don't know what it is.

I can definetly see my Livebox when I click on the dual-computer logo in the top right hand corner of the screen. It only lets me chose WPA and LEAP(?) options.

I am not aware of Orange LiveBox issues.  If you have internet references for this - let us have a look.

Are you sure it is WEP?  Network Manager detects encryption automatically.

To confirm:
```
iwlist scan
```

This will list all networks with encryption.

MAC filtering puts a hardware restriction on - so only specific wifi devices can connect (this is not a ssecure as it seems though).

---

### Post by Beaker Boy on 2008-02-11
I'm afraid iwlist scan gave me the response

lo           Interface doesn't support scanning
eth0      Interface doesn't support scanning
eth1      No scan result

However, mine and several other wireless networks are listed when I click on the Network Manager icon.  I know Orange Broadband don't support LINUX, but I was hoping for a work round.  Any more tips you can give me?

Many thanks

Alex

---

### Post by jrothwell97 on 2008-02-11
There shouldn't be a problem unless the router uses a non-standard form of wi-fi. As Linux uses normal TCP/IP, you should be OK connecting to the router.

You may need to switch on SSID broadcast, and turn off MAC filtering. You can do this (normally) by logging in to the admin panel of the router - the router's address is usually 192.168.1.1, so if you put that in your browser on a machine that *does* work, it may offer you a solution.

You might also want to try phoning Orange, but there is no need to tell them you're running Linux. The problem is that the router won't accept incoming connections from a certain device. Linux should have no bearing on anything.

---

### Post by karlo on 2008-02-11
> **jrothwell97 said:**
> There shouldn't be a problem unless the router uses a non-standard form of wi-fi. As Linux uses normal TCP/IP, you should be OK connecting to the router.

You may need to switch on SSID broadcast, and turn off MAC filtering. You can do this (normally) by logging in to the admin panel of the router - the router's address is usually 192.168.1.1, so if you put that in your browser on a machine that *does* work, it may offer you a solution.

You might also want to try phoning Orange, but there is no need to tell them you're running Linux. The problem is that the router won't accept incoming connections from a certain device. Linux should have no bearing on anything.

finally, don't remove ubuntu! :):lolflag:

---

### Post by Beaker Boy on 2008-02-11
Thanks for the info.  I've logged on to the configuration for the livebox but I can't see where you switch on SSID or turn of MAC filtering.  Any hints?

Beaker Boy

---

### Post by ugm6hr on 2008-02-11
I have never seen an Orange Livebox.  However, it should work just fine.

Unfortunately, documentation for it is a bit limited.  So there is a bit of guesswork in this.

First: [http://www.orange.co.uk/time/livebox/security.htm](http://www.orange.co.uk/time/livebox/security.htm)
Unclear whether this is WEP or WPA.  Given Network Manager (NM) recognises it as WPA - is it possible yours defaults to WPA?  Did you get given an encryption code with the Livebox?  If so - how many digits?  Is it ASCII or HEX?

Second: [http://www.orange.co.uk/time/livebox/setup_9.htm](http://www.orange.co.uk/time/livebox/setup_9.htm)
I am not certain what "pairing" is.  It sounds like an automated MAC filter to me.  I suspect you have to activate pairing (?by pressing button 1) prior to trying to connect with the correct encryption key.

If this doesn't work:
Try taking screenshots of all the Livebox setup pages and posting links here.

PS: There was no link in your PM.  Please post here rather than by PM.

---

### Post by Beaker Boy on 2008-02-11
Oops!  Sorry. The link I was trying to send you was 

[http://www.orangeproblems.co.uk/phpBB2/viewtopic.php?p=24492](http://www.orangeproblems.co.uk/phpBB2/viewtopic.php?p=24492)

This is from the orangeproblems webpage.

Many thanks

Alex

---

### Post by ugm6hr on 2008-02-11
Actually, it should be a lot simpler than that.

A guick google has revealed the problem (although it is mentioned in your link too):
[http://community.eu.playstation.com/showthread.php?t=75445](http://community.eu.playstation.com/showthread.php?t=75445)

The issue is that the Orange Livebox appears to use WEP and WPA at the same time.  Honestly, I didn't even know that was possible.  I am not sure it actually adds any additional security.

So - after all that - here is your (almost certain to be) solution:
[Solution Here]("http://help.orange.co.uk/documentDisplay.do?resultType=5002&docProp=$solution_id&groupId=1&directSolutionLink=3&gotoLink=0&page=&clusterName=DefaultCluster&docType=1006&docPropValue=kb12331")

This explains how to access the set-up without Windows (although I think you have already worked this out):
[http://zxon.notnet.co.uk/orange/manual_setup.html](http://zxon.notnet.co.uk/orange/manual_setup.html)

Make sure you have ethernet cable connected to do this.  After setting this stuff up, hopefully it should just work!  Remember, you will need to enter the correct WPA code, and still do the "pairing" thing (since it appears MAC filtering cannot be switched off, and MAC codes cannot be added manually).

Ref: [http://zxon.notnet.co.uk/orange/#1.1](http://zxon.notnet.co.uk/orange/#1.1)

---

### Post by Beaker Boy on 2008-02-11
SWEET!  Thank you so much everyone for all your help.  This appears to have done it.  This is the first message posted from my new LINUX laptop!!!  Life is good!!!

Many thanks

Alex

---

### Post by Beaker Boy on 2008-02-11
By the way, should I set this thread as solved or something?

---

### Post by ugm6hr on 2008-02-11
> **Beaker Boy said:**
> By the way, should I set this thread as solved or something?

Yes.  But I've done it for you on this occasion!

For future reference - it appears as an option under "Thread Tools" near the top of the forum post listing.

And welcome to Ubuntu online!

---

### Post by ugm6hr on 2008-02-12
> **Beaker Boy said:**
> By the way, should I set this thread as solved or something?
Had another thought....  It might be nice if you write a comprehensive How-To for other Ubuntu users of the LiveBox.  Some screenshots etc would make things clear.  I've just seen a few other posts with similar problems.

If you do get around to doing it - post it here: [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

If you are interested in network printing - this is interesting:
[http://ubuntuforums.org/showthread.php?t=540325](http://ubuntuforums.org/showthread.php?t=540325)

---

### Post by bigken on 2008-02-12
the easiest way to setup the orange live box is to switch of wep/wpa then pair your laptop/work station once you have a wireless connection turn the wep/wpa back on you will now be asked for the key just copy and paste and away you go

---

### Post by Beaker Boy on 2008-02-12
Good idea.  I'll jot some notes down and get it typed up.

---

