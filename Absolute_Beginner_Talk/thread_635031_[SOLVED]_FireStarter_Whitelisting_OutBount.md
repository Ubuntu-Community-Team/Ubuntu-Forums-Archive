---
title: "[SOLVED] FireStarter: Whitelisting OutBount"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-12-08
Hi, I really like Firestarter great GUI with good features. I'd like to
Block all outbound connections and just let things through I want.
I've changed Policy setting in the outbound section to WhiteListing.
If I have Firestarter up a running at the time will it state what port
to let through.  I know the main ports to let through such as http, pop,
Secure IMAP.  There are times I'm sure when I want to know what port
a program I need wants such as Gaim/Pidgin. Will it let me know as it's
trys to access so I can let it through?

---

### Post by ruibernardo on 2007-12-08
> **Orbital75 said:**
> There are times I'm sure when I want to know what port
a program I need wants such as Gaim/Pidgin. Will it let me know as it's
trys to access so I can let it through?

Hi orbital75,

I think you see that in the events tab. There will be a connection coming from your computer to an externet IP that will be logged as blocked. Right-click on that event and select what kind of permission you want to give.

---

### Post by Orbital75 on 2007-12-08
Thanks..... Didn't realize it was so simple....  :)

---

### Post by Orbital75 on 2007-12-08
Got a quick Question......  If I wanted to allow File Sharing (Samba) 
Do I allow it Outbound or Inbound?  Don't want to do anything to
compromise myself..... I have a NAT Router so I should still be safe
file sharing internally.  :)

---

### Post by Dr Small on 2007-12-08
Will you PLEASE stop worrying about security!? :D I think you are paranoid.
Anyhow, to allow Samba, to your system, that would be incoming.
If your system was the router and firewall, and everyone passed through your system, then you would need to enable Samba for outgoing too, that way other systems can connect to each other.

Dr Small

---

### Post by Orbital75 on 2007-12-08
> **Dr Small said:**
> Will you PLEASE stop worrying about security!? :D I think you are paranoid.


Guess it's just the windows in me.....   :)

---

### Post by ruibernardo on 2007-12-08
It's not thaaat paranoid.

If you only install opensource software from trusted sources (ubuntu repos or from sources), you shouldn't be afraid and you can allow outbound policy. When an opensource application has a security flaw, it is reported and many people help to make it right. The problem only rises when you install closed source applications.

So if you only install binaries from Ubuntu repositories, you're safe. If you don't, you have two choices: blindly trust who made that binary or compile it yourself.

If you install closed source binaries you only have two :-s choices: blindly trust who made that binary or block all outbound connections to see if it makes any strange connection.

I'm not paranoid myself, but I have a little story about closedsource software back in 2005. Don't know if anybody remembers this.

I installed what was back then the first msn client with webcam support on non-windows platforms: mercury. It was (is?) a closed source java application and I had Firestarter in the mode that orbital75 was using. I also used other msn clients and had it working, but with mercury I couldn't because it refused to connect. I went and checked Firestarter logs and saw a "misterious" connection that was being blocked. It was originated by mercury. Mercury was calling home :o... and it didn't connect to msn if that call wasn't made! Back then a thread at mercury forum was open about it and Danny (the main developer) said it was a statistical connection. I remember talking about in at IRC channels here in Portugal and nobody knew about it, and when people found the thread in the forum, nobody used mercury anymore. 

No more binaries from not trustful repositories or closedsource software here since then any more - just compiled by me or from ubuntu repositories. Mercury never got the success it could had after this little episode.

---

### Post by Orbital75 on 2007-12-10
Yep, that's exactly my point. Not worried about the repositories at all just the Apps that
I have to load with Wine or non-open programs that do what I need that I can't find
a replacement for that's open.

---

