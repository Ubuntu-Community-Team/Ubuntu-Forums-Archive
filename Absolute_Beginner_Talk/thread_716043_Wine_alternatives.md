---
title: "Wine alternatives"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by watsgoodg on 2008-03-05
I did a search and was not able to find what i was looking for.  I just rebuild my ubuntu dual boot windows xp machine.   I had a program called wine something.  I have wine installed as well.  I am having a problem remoteing into my xp machine via rdp.  But from windows xp i can remote into it no problem.  I think the wine program i had installed played a key role in this.  So if someone can tell me what the alternative is i would appreciate it thanks.

---

### Post by jimv on 2008-03-05
What is the problem specifically?  Is it giving an error message when you try to RDP in?  I use my Ubuntu install to log into my XP machine all the time.  WINE should not be needed.

---

### Post by neurostu on 2008-03-05
there is a program called crossover, which is essentially a commercial version of wine that is automated and supports specific applications. You might want to check it out!

---

### Post by watsgoodg on 2008-03-05
it will not allow me to remote in.  I turned off the firewall on ubuntu and still nothing.  I boot into windows and im able to remote in using remote desktop?

---

### Post by dca on 2008-03-05
I'm confused, your dual-booting w/ XP and when logging into Ubuntu you're trying to access the XP side?

---

### Post by dca on 2008-03-05
If you're trying to remote access a WinXP machine (that's not your own when logged into Ubuntu), you should be able to use the 'Terminal Server Client' app installed into your 'Applications -> Internet' menu.  Make sure you select 'RDP' as the protocol...

---

### Post by arochester on 2008-03-05
> I had a program called wine somethingWine-doors?

---

### Post by watsgoodg on 2008-03-05
Sorry im not being clear.  point A I have a dual boot machine with xp and ubuntu.  I am trying to remote into a machine in point B.  Point A booted into xp i can remote to point B.  From ubuntu i cant.  I had it setup where i had remote desktop installed on wine. and if forgot the other wine application i had running and it worked.

---

### Post by stchman on 2008-03-05
> **watsgoodg said:**
> I did a search and was not able to find what i was looking for.  I just rebuild my ubuntu dual boot windows xp machine.   I had a program called wine something.  I have wine installed as well.  I am having a problem remoteing into my xp machine via rdp.  But from windows xp i can remote into it no problem.  I think the wine program i had installed played a key role in this.  So if someone can tell me what the alternative is i would appreciate it thanks.

You can use a program called VNC.  It allows either OS to remote in.  VNC is installed in Ubuntu by default and you can et it for XP.

---

### Post by watsgoodg on 2008-03-05
yes im aware of that thanks.  So basically no one knows an alternative for wine?>

---

### Post by sancho panza on 2008-03-05
I too am confused by why you need wine so badly. Wine is not required to connect from ubuntu to xp via remote-desktop. If the XP machine is in a secure network, you might need something like VPN (virtual private network) on your ubuntu machine before accessing the xp machine.
I, like others, do not understand why wine is necessary here.

---

### Post by jimv on 2008-03-05
Is RDP giving you a paticular error message?  I think there are two RDP selections to choose from when you use the RDP client in Ubuntu...rdp and rdp-5.  Try both.  Also, try putting the remote computer's name in front of your login name, so it would look like "computername\username" when logging in.

Once again, you don't need WINE at all.  I remote into my work computer all the time from my ubuntu laptop using tsclient.

---

### Post by watsgoodg on 2008-03-06
The error im getting:  "An error has occured Auto Selected keboard connect: connection refused.  

What i dont understand when i use putty and remote desktop from my xp machine it works fine?  I am able to remote in fine...

---

### Post by Mauler5858 on 2008-03-06
Crossover linux is an option, HOWEVER it is not free.

[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

---

### Post by watsgoodg on 2008-03-06
> **Mauler5858 said:**
> Crossover linux is an option, HOWEVER it is not free.

[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

Thanks for the reply...there was a program similar to wine it might have even been part of wine but i forgot the name of it...i have it installed on another machine ill find out the name and let you guys know what it is.  Then ill install and see if this resolves the problem.

---

### Post by AndyCooll on 2008-03-06
> **watsgoodg said:**
> I did a search and was not able to find what i was looking for.  I just rebuild my ubuntu dual boot windows xp machine.   I had a program called wine something.  I have wine installed as well.  I am having a problem remoteing into my xp machine via rdp.  But from windows xp i can remote into it no problem.  I think the wine program i had installed played a key role in this.  So if someone can tell me what the alternative is i would appreciate it thanks.

This "should be" an issue more to do with rdp rather than Wine. In effect it seems to me that you're trying to circumvent the rdp problem by running an alternative app under Wine.

I'd be more interested to know what issues you had using the Terminal Server Client. And for that there are also alternatives such as TightVNC.

:cool:

---

### Post by watsgoodg on 2008-03-06
> **AndyCooll said:**
> This "should be" an issue more to do with rdp rather than Wine. In effect it seems to me that you're trying to circumvent the rdp problem by running an alternative app under Wine.

I'd be more interested to know what issues you had using the Terminal Server Client. And for that there are also alternatives such as TightVNC.

:cool:

The things thats bothering me is i had it working on another ubuntu machine.  Same version same configs.  The only thing i had difference was this program that i cant figure out what it was.  As of right now i will leave it alone until i find that program.  If its 2 much of a hassle like i said i have a dual boot i can boot into xp and just remote from that os.

---

### Post by gecko113 on 2008-03-06
Well here is something else like Wine but just as good. It sets up like boot camp where u can have another OS going while linux is going. If u have any more info on it check the link out. It also tells you how to install it.
 [http://www.techthrob.com/tech/linux_virtualization.php](http://www.techthrob.com/tech/linux_virtualization.php)

---

### Post by watsgoodg on 2008-03-06
> **gecko113 said:**
> Well here is something else like Wine but just as good. It sets up like boot camp where u can have another OS going while linux is going. If u have any more info on it check the link out. It also tells you how to install it.
 [http://www.techthrob.com/tech/linux_virtualization.php](http://www.techthrob.com/tech/linux_virtualization.php)

wow thank you for the reply...i have been using vmware on my xp box for a long time.  I wasn't aware that it was compatible for linux.  If all goes well i can finally totally migrate to linux and do away with xp ):P.

---

### Post by AndyCooll on 2008-03-06
> **watsgoodg said:**
> wow thank you for the reply...i have been using vmware on my xp box for a long time.  I wasn't aware that it was compatible for linux.  If all goes well i can finally totally migrate to linux and do away with xp ):P.
Indeed we have a whole section of these forums dedicated to this sort of thing: [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308")

:cool:

---

### Post by watsgoodg on 2008-03-07
Found the app that i needed.  It is called wine - doors.  Anyone ever hear of it?

---

