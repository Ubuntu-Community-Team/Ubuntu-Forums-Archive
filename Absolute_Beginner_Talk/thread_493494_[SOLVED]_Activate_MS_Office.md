---
title: "[SOLVED] Activate MS Office?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-07-05
I had a copy of MS Office 2003 sitting around and just for kicks, I wanted to see if I could install it through Wine. 
Everything works perfectly with Wine 0.9.40 (installation, running office). But one minor problem: How do I activate the product? Everytime I try it says it can't connect or something. So I though I would do it via telephone, but that solution doesn't seem to work either. Can anyone help me out?

---

### Post by razeshkale on 2007-07-07
First thing i dont understand y ur trying to install that MSheet on this gr8 os!!

Activation Activation !!!!@@@@@

---

### Post by isaacj87 on 2007-07-07
Haha...yeah I know. But I just wanted to see if Office could actually work with wine. Anywho...Activation?!

---

### Post by Jimmyfj on 2007-07-07
> **isaacj87 said:**
> Haha...yeah I know. But I just wanted to see if Office could actually work with wine. Anywho...Activation?!

Sudo activate my openoffice for free -f

Why not use the best? OpennOffice.org

---

### Post by Tadpole on 2007-11-22
The responses to this guy are horrendous. *He wants to install MS Office, not OpenOffice.org.* How ******* arrogant can you people be.

*takes a deep breath*

I have the same issue. I'm trying to activate MS Office on Wine 0.9.37 (the latest version that works with it, apparently). It won't activate over the internet and the boxes are grayed out when you try to activate over the phone. If anyone has any tip to solve this, I would really appreciate it.

---

### Post by kpkeerthi on 2007-11-22
This appears to be a a known [ wine bug]("http://bugs.winehq.org/show_bug.cgi?id=9944"). 

I found this comment in the bug report. I'm just posting it here although I have no idea what it means. You will have a better luck in wine forum, I guess.

```

I encountered the same issue when attempting to activate in Wine 0.9.49,
compiled from the tarball. The issue displayed in an identical manner to the
picture attached to this bug. [B]I fixed the issue by overriding riched20 and
riched32 with the native setting. That change allowed the country select box to
appear. Once the country was selected, the activation boxes ungrey and the
activation may continue.[/B]

```

---

### Post by natehatewindows on 2007-11-22
lets chill out little tadpole. no need to get all upset...people are just being honest. and trying to give him a easy solution that has the same (well better) results ;)

---

### Post by Tadpole on 2007-11-22
THANK YOU kpkeerthi! I actually read that comment in the bug report previously but I didn't really take it seriously until you mentioned it. All you need to do is go to winecfg, click the Libraries tab, and add both "riched20.dll" and "riched32.dll". Then close all MS Office windows and reopen one again. Choosing the telephone option now provides a drop-down to choose your country of origin, which then ungrays the boxes.

Excellent.

And for you, natehatewindows, it is incredibly presumptuous to categorically dismiss MS Office in place of OpenOffice.org. My sister wants it because OO.org doesn't always read her Word documents perfectly. YMMV, but if someone asks for help installing MS Office, you either help them or *shut up*. Responding with something like "y ur trying to install that MSheet on this gr8 os!!" makes you sound like an incredible douchebag.

---

### Post by kpkeerthi on 2007-11-22
@tadpole
Were you able to activate your copy now?

---

### Post by Tadpole on 2007-11-22
> **kpkeerthi said:**
> @tadpole
Were you able to activate your copy now?
Yes, I did it over the phone.

---

### Post by kpkeerthi on 2007-11-22
Awesome.

---

### Post by hyper_ch on 2007-11-22
> **Tadpole said:**
> YMMV, but if someone asks for help installing MS Office, you either help them or *shut up*. Responding with something like "y ur trying to install that MSheet on this gr8 os!!" makes you sound like an incredible douchebag.

People may not know about alternatives and hence what nathanhatewindows did is correct. You see, your sometimes so into a specific problem that you don't consider alternatives hence I support the mentioning of OOo.

Just for the records, a friend of mine had to submit her master thesis yesterday and M$ Office XP just behaved strangely. She wanted to have two pages in landscape with a table accross those two. Guess what happens? M$ Office didn't show any footnotes after those two landscape pages with the table... OOo however displayed it perfectly.

So mentioning alternatives - even if people are asking about a specific program - is, IMHO, never out of bounds - au contraire to your reply to nathanhateswindows, which I think was very inappropriate.

---

### Post by AlanRogers on 2007-11-22
> **razeshkale said:**
> First thing i dont understand y ur trying to install that MSheet on this gr8 os!
 
> **Tadpole said:**
> And for you, natehatewindows, it is incredibly presumptuous to categorically dismiss MS Office in place of OpenOffice.org... Responding with something like "y ur trying to install that MSheet on this gr8 os!!" makes you sound like an incredible douchebag.
 
> **hyper_ch said:**
> So mentioning alternatives - even if people are asking about a specific program - is, IMHO, never out of bounds - au contraire to your reply to nathanhateswindows, which I think was very inappropriate.
I'm not a moderator on this forum but I am on elsewhere and, whilst I agree that the content of the original reply was a valid response, the tone of it was completely inappropriate. Thankfully, it was taken in the spirit in which I like to think it was intended but this is a multi-cultural, multi-lingual, multi-nationality forum and humour is very difficult to articulate in the written word, due to the lack of facial expression and body language. Emoticons don't cut IMHO, and people should be wary, especially when using SMS-style abbreviations.
 
I'm just glad that this thread reached a solution. Well done for raising it; I learned something.

---

### Post by natehatewindows on 2007-11-22
> **Tadpole said:**
> THANK YOU kpkeerthi! I actually read that comment in the bug report previously but I didn't really take it seriously until you mentioned it. All you need to do is go to winecfg, click the Libraries tab, and add both "riched20.dll" and "riched32.dll". Then close all MS Office windows and reopen one again. Choosing the telephone option now provides a drop-down to choose your country of origin, which then ungrays the boxes.

Excellent.

And for you, natehatewindows, it is incredibly presumptuous to categorically dismiss MS Office in place of OpenOffice.org. My sister wants it because OO.org doesn't always read her Word documents perfectly. YMMV, but if someone asks for help installing MS Office, you either help them or *shut up*. Responding with something like "y ur trying to install that MSheet on this gr8 os!!" makes you sound like an incredible douchebag.


when did i say that? i dont think i did....maybe you should read a little closer ;) and hey...i would watch what you say,,,dont want to file a complaint against you....there are kid here and that language offends me :)

---

### Post by isaacj87 on 2007-11-23
Whoa whoa everyone...

Let's all just settle down and be friendly with one another...I haven't paid attention to this thread in awhile and I was not aware of the recent activity!

I've been using Ubuntu for almost a year now and I *know *what free alternatives are available, in fact I use OpenOffice *frequently* to complete schoolwork. I mean, honestly, how could you not know OpenOffice wasn't installed by default? It's one of the most publicized features of Ubuntu!  I was just bored, had a copy of Windows Office 2003 from another lifetime ;) , and wanted to see if I could get it running in Wine....so it was a little grating to have people telling me to use something I already use...and not remain on topic. Thank you Tadpole for reminding others (although, next time be a little nicer...lol)  and for the telephone solution! I will try that out later... :)

Thanks to everyone who replied. That's one of great things about this community...You never feel lonely... ;)

P.S. I've also found another solution to getting Office to work with later versions of Wine...It's not pretty, but it works. Basically, install Office on the latest Wine version, then uninstall Wine and download the deb for Wine 0.9.37, install that...run Office and then reinstall the latest version of Wine..voila.

Marking thread as solved...:D

---

### Post by isaacj87 on 2007-12-29
Thought I'd revive my thread just in case anyone cared...

I just updated to WINE 0.9.52 and I was able to perform the online activation with no workarounds. Office 2003 works flawlessly now! Now this thread really can be marked as solved. :)

---

