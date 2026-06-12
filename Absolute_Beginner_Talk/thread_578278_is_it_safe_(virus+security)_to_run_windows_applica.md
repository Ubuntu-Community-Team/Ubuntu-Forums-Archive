---
title: "is it safe (virus+security) to run windows applications with WINE?"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by genbuntu on 2007-10-17
Hi

I was wondering how vulnerable ( 'virus-wise' and 'security-wise' ) would my ubuntu be if I ran windows programs with Wine.  Would windows p2p programs  decrease the security-level of my system?

---

### Post by FredB on 2007-10-17
Not vulnerable at all. But there are great linux based p2p client. Why bothering with windows programs ?

---

### Post by julian67 on 2007-10-17
If you run windows applications in wine and collect some malware it could mess up your .wine folder/environment but it shouldn't impact the rest of your system

---

### Post by Sef on 2007-10-17
> If you run windows applications in wine and collect some malware it could mess up your .wine folder/environment but it shouldn't impact the rest of your system

If it was a MS Word virus, it could affect any document saved as a word file (.doc.)

---

### Post by genbuntu on 2007-10-17
Ok; how about the 'internet security' of my system. I assume it might open some ports. 
For e.g. I want to try 'Joost' (p2p video) on Ubuntu with Wine.

Thanks

---

### Post by julian67 on 2007-10-17
> **genbuntu said:**
> Ok; how about the 'internet security' of my system. I assume it might open some ports. 
For e.g. I want to try 'Joost' (p2p video) on Ubuntu with Wine.

Thanks

yes, same as any p2p it's going to make you very visible so you need to feel confident that your p2p application isn't vulnerable.  You probably should be behind a router with firewall or install something like firestarter.  I used to use utorrent with wine and didn't have any problems afaik.  I think you can find similar free applications like joost. This looks a lot like miro to me.

[http://www.getmiro.com/]("http://www.getmiro.com/")

---

### Post by Sef on 2007-10-17
> You probably should be behind a router with firewall or install something like firestarter.

Ubuntu comes with a firewall installed: IPTables.   Firestarter is just a GUI front end for it.

---

### Post by genbuntu on 2007-10-17
1) So is there anything I can do to iptables/firestarter to make it safer?

2) I downloaded Miro but didn't like it . (One has to download before watching plus the breadth is not quite same as that of 'Joost' ).

---

### Post by erginemr on 2007-10-17
That is also the reason why I feel I should stay away from Wine. I have read somewhere that apart from the .wine folder, virii or trojans can wreak havoc in your whole home folder but cannot touch the other system folders, because of intrinsic linux file/folder ownership rules. Is this true?

I would also vote for Firestarter as a secondary layer of security shield. IPTables may have been already installed and active, but I made a test before and after installing Firestarter by visiting the famous "Shields UP!" site ([http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2)). And the ports shown as "Closed" before, have been reported as "Stealth" after the activation of Firestarter as a firewall. 

So, my second question is; is there a way to "stealth" your ports via IPTables config files without installing Firestarter as a GUI?

---

### Post by julian67 on 2007-10-17
> **Sef said:**
> Ubuntu comes with a firewall installed: IPTables.   Firestarter is just a GUI front end for it.

Yes people often mention this when a firewall is suggested. But what doesn't get stated clearly enough is that iptables is *unconfigured* and > **When you install Ubuntu, iptables is there, but it allows all traffic by default.** (my bold)

source: [https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")

I can promise you that on a default install when you run the command 

```
sudo iptables -nL
``` the result you get is

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

=all traffic allowed ;-)

When you start using p2p applications you become extremely visible and you get all kinds of unwanted connection attempts. If your PC is sat there online with  an (possibly unsupported and untrusted) application listening on multiple (or even unknown random) ports you really should have some control over the traffic. So you can learn iptables or use a gui frontend, hence my suggestion to use Firestarter or similar. For a desktop user a nice gui interface fits the Ubuntu philosophy much better than expecting users to correctly set iptables rules by hand and it's very easy and quick to set up. If you don't have iptables configured one way or the other your security policy comes down to only using invulnerable applications (no, I can't think of any either) and unbreakably strong passwords. Good luck.

edit: it also pays to remember that a p2p application is by definition not only listening, it is actively seeking connections to other peers/servers/nodes. Some p2p apps even use multiple p2p protocols and might also initiate connections via your browser for searches of indexing sites. Some even use all available ports including normal service ports like 25. .

---

### Post by genbuntu on 2007-10-17
Thanks Julian, that was insightful.

---

### Post by Kilz on 2007-10-17
You might not be thinking about it. But using p2p, even with a firewall, it will be possible to see exactly who you are and what you are sharing. Be very careful to not have any copyrighted content in your share folder. Some lady recently lost a case and may end up paying 220k because supposedly her p2p application indexed the folder she stored ripped cd's in.

---

### Post by HermanAB on 2007-10-17
A MS Word macro virus may be able to do some damage, but in all the years that I have been running Linux and Wine, I have never had a problem.  Most regular programs won't even run on Wine, so the chances of a virus running on it is rather remote!

---

### Post by tzembi on 2007-10-18
Short answer:
Windows applications work the same way in Wine as they do in Windows. So in short: 
Yes - Security is an issue.

Long answer with infos:
[http://ubuntuforums.org/showthread.php?t=543419](http://ubuntuforums.org/showthread.php?t=543419)

---

### Post by bodhi.zazen on 2007-10-18
This seems to be an age old discussion.

My general comments are that many of your links are old and outdated.

Wine != Windows and although an exploit is possible, Wine HQ is aware of potential problems and does patch code.

_Windows virus on Linux_: At this time it is possible to run windows viruses with wine. They do not run well yet.

		[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

This is my response to your post:

 [http://ubuntuforums.org/showpost.php?p=3094631&postcount=25](http://ubuntuforums.org/showpost.php?p=3094631&postcount=25)

You can read the thread if you like ^^

		[http://software.newsforge.com/article.pl?sid=06/04/18/1941251&tid=78](http://software.newsforge.com/article.pl?sid=06/04/18/1941251&tid=78)

Additional info : [http://www.linux.com/article.pl?sid=07/02/13/1637251](http://www.linux.com/article.pl?sid=07/02/13/1637251)

In summary :

1. Is it possible that running windows applications with wine may represent a security threat ? Yes, but no more so then any other application.

2. WineHQ, and others, are proactive regarding security, but they of course can not promise absolute security.

3. At this time there is no known threats from windows applications on wine. If a threat is identified it should be reported to Ubuntu or winehq and, as others before it, they will be patched.

4. DO NOT RUN WINE AS ROOT.

---

### Post by genbuntu on 2007-10-18
> **Kilz said:**
> You might not be thinking about it. But using p2p, even with a firewall, it will be possible to see exactly who you are and what you are sharing. Be very careful to not have any copyrighted content in your share folder. Some lady recently lost a case and may end up paying 220k because supposedly her p2p application indexed the folder she stored ripped cd's in.

Oh, thanks for that cautionary note Kilz. I didn't know that could also happen.

---

### Post by genbuntu on 2007-10-18
I've posted the question (below) on another thread: ([http://ubuntuforums.org/showthread.php?p=3556767&posted=1#post3556767](http://ubuntuforums.org/showthread.php?p=3556767&posted=1#post3556767) ) . Interested reader may refer to that also.

"  I recently realized another cause of concern. Since I have dual boot with Windows XP , now how different (insecure) is that compared to using Wine on only ubuntu installed machine.
Are there greater chances of a virus doing damage to my windows partition from within Wine running under ubuntu? "

---

