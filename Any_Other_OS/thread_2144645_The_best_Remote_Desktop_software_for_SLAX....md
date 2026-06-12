---
title: "The best Remote Desktop software for SLAX..."
date: 2013-05-13
forum: Any Other OS
---

### Post by fatboy123 on 2013-05-13
A Quick question first, my understanding of Linux as of now is that **Linus Torvalds** developed the kernel and now all the other distributions and variation of hundreds of Linux version all share the same kernel as the one **Linus Torvalds** created, am I correct? 

It's like any programmer can just take the kernel, customize with different desktops and programs and put a name on it like gugubuntu or something ???

So any Linux software for any version will work on any other Linux version?

In that regard, I'm using SLAX off of a USB drive just to use basic banking in internet cafes, and I need a software to connect to my windows 7 machine back home to see the desktop and share files, what are my choices? what is the best software I should download?

Thanking you all in advance.

Bobak.

---

### Post by DuckHook on 2013-05-13
> **fatboy123 said:**
> A Quick question first, my understanding of Linux as of now is that Linus Torvalds developed the kernel and now all the other distributions and variation of hundreds of Linux version all share the same kernel as the one Linus Torvalds created, am I correct?

This is like saying that Einstein developed relativity and now all of physics is based on relativity for all of its workings. Such a description is oversimplified. Linux has grown so much beyond its creator, just as physics has grown so much beyond Einstein, that, revered historical figures though they be, it would be a mistake to equate them with the new world that they created.

> It's like any programmer can just take the kernel, customize with different desktops and programs and put a name on it like gugubuntu or something ???

The kernel is actually a very small part of any distro. It is the most critical part and the foundation upon which everything else is built, but it is to a distro what a heart and brain is to your body. You would no more define the whole person that you are as just a heart and a brain than a distro is defined as just the Linux kernel plus some stuff.

> So any Linux software for any version will work on any other Linux version?

It can be gotten to work, but is not wise. For example, Ubuntu uses apt to manage apps and repositories. Fedora uses YUM. Arch uses pacman. Etc. Also, configurations vary tremendously between distros. A config file for Arch is highly unlikely to work in Ubuntu and vice versa. To extend the bodily analogy, livers are not easily interchangeable between different people.

> In that regard, I'm using SLAX off of a USB drive just to use basic banking in internet cafes, and I need a software to connect to my windows 7 machine back home to see the desktop and share files, what are my choices? what is the best software I should download?

You should stick to SLAX repos and not go mixing in Ubuntu apps. The installation routines, default config files, dependencies are all wrong. High-level users do mix and match sometimes, but it takes lots of learning by trial and error, knowing how to reconfigure and knowledge of the intricacies of each distro and app. One should really heed the "for advanced users" sign on this one.

SLAX, like all distros, has its own community and forums. You should post your question there, and I'm sure SLAX users would be happy to guide you.

---

### Post by DuckHook on 2013-05-13
> **fatboy123 said:**
> ...I'm using SLAX off of a USB drive just to use basic banking in internet cafes...

I can't help adding that if you are doing your banking at Internet Cafes, you have far larger worries than the nature of Linux and the relationships between distros. You are engaging in one of riskiest behaviours that I know of and should expect your bank account to get zeroed out someday soon, if not worse.

In my opinion, the only semi-secure way to use an Internet Cafe is to tunnel a VPN to either a VPN provider or back to a VPN server at home. Anything short of this is simply juggling with fire. I do hope that you start practising much safer computing especially when it comes to stuff like banking. I would never do banking even over a VPN at an Internet Cafe.

---

### Post by fatboy123 on 2013-05-13
DuckHook,

Thank you very much for your lucid explanation, it's starting to make sense to me now bit by bit.

I'm traveling next month and have some simple banking like paying rents and credit card debits and so on, the ONLY reason I came to Linux was because somewhere I read that by using a LIVE USB and loading the OS into ram, then I would be totally safe from malware, so while I'm abroad, I can just use any internet cafe to load my OS into ram and be safe !!! 

If even this is risky then I'm lost, what else should I do then ???

Bobak.

---

### Post by DuckHook on 2013-05-13
> **fatboy123 said:**
> ...simple banking like paying rents and credit card debits and so on...If even this is risky then I'm lost, what else should I do then ???

1. Full disclosure: I've been called paranoid on these forums and among friends for good reason--I practice a level of security that most people don't. So some will consider my warnings to be overkill.

2. The problem is not your OS so the main worry is not malware; the real problem is the Internet Cafe or any other public WIFI Hotspot. Even if they offer encryption, you will be sharing your connection with every other patron, which means that it may as well be unencrypted. It is child's play to sniff every data packet within a WIFI zone, especially if one knows the encryption key. In my opinion, it is actually better for Cafe's to not encrypt their connections so that people are not misled into a false sense of security. Most do so to deter non-paying public than for any real security.

3. That is why I recommended VPN. If you must use public WIFI spots, the best way is establish a secure VPN tunnel with either a provider or a VPN server at home. Once you do so, then *all* traffic from your laptop is encrypted from end to end. Anyone sniffing your data packets just get garbled nonsense. It is still theoretically possible to decrypt such traffic, especially if you use a lousy protocol or poor encryption passphrases, but even if you just increase the level of difficulty, bad guys will usually go after easier pickings (which are plentiful in an Internet Cafe).

The drawback to VPN, especially for new users, is its relative complexity. [Here]("https://help.ubuntu.com/community/OpenVPN") is an Ubuntu link to setting up a VPN. It won't work with STAX, but they may have simple instructions for setting up their VPN stack. [Here]("http://openvpn.net/index.php/open-source/documentation/howto.html") is a more in-depth link from the OpenVPN site itself. For a simple, but dated explanation of VPN, look [here]("https://help.ubuntu.com/community/VPNClient").

There are third-party VPN providers who will sell you VPN access so that you don't have to set up your own VPN server at home. You might consider them a worthwhile investment at least for the period during which you are travelling. They usually have instructions on how to connect to their services using Linux. I would also highly encourage you to pose this question on the STAX forums, look at their community documentation and, of course, make liberal use of Google.

A further alternative is to continue using Windows because most VPN providers have good GUI-based installers for Windows. 

Last but not least, if it is practical to avoid public hotspots altogether (at least for banking use) then this is best. You can get away with not really caring about typical surfing (like looking up restaurants, etc). It's just stuff that involves user IDs and passwords that you want to avoid. For example, a ***wired*** connection at your hotel is safer than a public hotspot. Beware of hotel WIFI which is every bit as lousy--perhaps even lousier--crackers have a lot more time and resources in the privacy of their hotel room snooping on the data packets of others.

Gook luck and happy travels!

---

### Post by squakie on 2013-05-13
Nothing paranoid about you DuckHook!  I can't agree more.  There is a false conception among some casual users that since Linux is far less vunerable to viruses, etc., that they are "safe" using it for things the poster here has mentioned:  doing very personal work with very sensitive data from any form of public network.  If just isn't safe.  I personally don't do anything but browse the net on a public network - I don't even check my mail.  None of these networks are safe.  I wouldn't even *THINK* of doing banking, bill paying, etc. - as you have mentioned that is just waiting for your bank account to cause you real problems.  As for remote desktop - I'm wouldn't do that from any public network as well.  DuckHook is 100% on.  If you are going to be gone for an extended period, I would seriously consider setting up automatic payments.

---

### Post by DuckHook on 2013-05-13
Thanks for the vote of confidence, squakie.

@fatboy123,

Yet another alternative is to connect over a tethered cellphone or do your banking through your phone, which a lot of banks will allow through their phone apps. Any phone data connection is secured quite well, so you won't have the same snooping concerns as public hotspots.

---

### Post by Bucky Ball on 2013-05-13
*Thread moved to **Other OS/Distro Support**.*

... with parts in Networking & Wireles, Security Discussions and The Cafe. Please use separate threads for each question and in the appropriate forums. It saves confusion. ;)

---

### Post by fatboy123 on 2013-05-14
Wow DuckHook,

Thank you so much for the write up and the immense knowledge you've empowered me with. 

I was under the impression that when using Firefox under "Private Browsing" and using HTTPS everywhere and the NoScript Security Suite addon, that all my pages would be highly encrypted BEFORE leaving my end so that even if it gets intercepted in between my PC and the internet cafe router, it would be useless.

Thanks for opening my eyes and giving me a whole lot of other things to worry about :(

Bobak.

---

### Post by DuckHook on 2013-05-14
Perhaps my "paranoia" is coming to the fore. So do take what follows with a grain of salt.

HTTPS does encrypt your communication, but no security scheme is 100% tight. One of the biggest dangers in a wireless setting is the man-in-the-middle attack. Roughly speaking, a bad guy fools the router into redirecting packet requests through his computer, or fools you into treating his computer as the router (before eventually passing your requests through to the actual router). If he can additionally spoof a certificate authority, then he has effectively bypassed https. The Electronic Frontier Foundation is a great organization that seeks to protect us from baddies. [This]("https://www.eff.org/deeplinks/2011/10/how-secure-https-today") report of theirs on https security is somewhat dated, but still relevant. It is important to note that these exploits are non-trivial. They require a high level of skill. The likelihood that someone is doing this stuff at any given wireless hotspot is small. But it is not zero. And when it comes to stuff like banking, I'm not happy with even a small exposure. But that's just me.

At least an equal danger, if not a bigger one, is the fact that not all banks/financial institutions implement https completely or properly. I've visited at least some sites that pass info from their supposedly secure https site onto plain http pages. You have probably run into this warning before in your own browser. We have no idea what pieces of info are leaking from the https protocol. It's probably innocuous stuff, but the fact that I don't know bothers me, and I don't like taking chances if I can help it.

The biggest danger, at least to my mind, is being lulled into bad habits. We are all creatures of habits. If we get used to doing our banking from a wireless hotspot, how long before we forget and start doing unsecured e-mail? What about those nasty things you're saying about your boss? The medical report your doctor just sent you? The racy exchange you are conducting with your significant other?

Nope. Call me paranoid, call me alarmist if you like. This is one bear who will continue to treat public WIFI hotspots with the same care as I would public restrooms, thank you very much.

BTW, your web measures are very laudable. If interested in security, the security section of this forum is very informative. You can also look at these links. Again, they deal with Ubuntu, but can be extrapolated to any distro; even Windows.

Basic Security:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

Advanced Security:

[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
all stickies in:
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)
in particular:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
and anything by bodhi.zazen, Dangertux, Ms Daisy

---

### Post by fatboy123 on 2013-05-15
Thanks again DuckHook, Now I know that even taking my OWN safe laptop with me is not an option as even THAT is not safe !!! I will spend some time reading those links you sent and bringing myself up to par.  Cheers.  Bobak.

---

### Post by DuckHook on 2013-05-15
The opposite issue is that we get so frozen with fear that we stop using otherwise useful tools. I would hate to see my warnings lead you there. For what it's worth, I take my laptop travelling. But my important info is encrypted, I tether to my phone if I'm in the middle of nowhere, and if I'm using a hotel connection, I VPN to my home router (which acts as a VPN server). These measures should be sufficient to protect almost all of us from baddies. Contrary to the Hollywood stereotype, there aren't that many genius crackers out there and those that qualify are either working for the NSA or trying to break into it. If you have one of them after you, then you have far bigger things to worry about than your bank account.

Keep in mind that security is not an absolute. You are never going to achieve total security, so that shouldn't be your goal. Also, as the security gurus on this forum are fond of saying, it's a process; not a program. If you keep hardening your computer in layers and learning good security practices, there is no reason why you can't take your laptop with you everywhere and still be safe and secure.

Good luck and hope the Slax forums prove welcoming and helpful!

---

### Post by fatboy123 on 2013-05-15
What do you think of TOR ??   [https://www.torproject.org/](https://www.torproject.org/)      They have a LiveUSB download preconfigured to bank safely anywhere, all data passes through their VPN and the USB live system that aims at preserving your privacy and anonymity. It helps you to use the Internet anonymously almost anywhere.  Any insights? if STILL unsafe, would it then the SLAX I'm using at the mometnt?      I'm sorry for taking so much of your time, this I think is my last question.  Bobak.

---

### Post by DuckHook on 2013-05-15
I have TOR installed. It is not a VPN but a community proxy anonymizer. Roughly, it strips originating identifying addresses from your data packets and then redirects traffic through fellow users who agree to act as relays. It is an incredible tool for maintaining privacy (a related issue to security, but not the same) and getting around the censorship that exists in some countries, but it is not an encryption technology and will not solve your public hotspot issue. If you wish to browse, e-mail and chat anonymously, then TOR is what you need. If you want to foil packet sniffers in a WIFI hotspot, then it won't do anything for you.

[Here]("http://netforbeginners.about.com/od/readerpicks/tp/The-Best-VPN-Service-Providers.htm") is a list of VPN providers that I've just Googled. Because I've set up my own VPN server at home, I don't know anything about these so you will have to research them yourself. Note that some are not actually VPN providers but anonymizers like TOR, which is not what you want. Also, avoid PPTP because it is an awful protocol that doesn't count as real encryption.

---

### Post by fatboy123 on 2013-05-16
Thanks again, you have been a tremendous help in opening my eyes. I will spend some time researching all this and hopefully coming up with an alternative.

---

