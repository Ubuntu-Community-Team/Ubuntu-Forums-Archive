---
title: "Mac On Linux..."
date: 2005-06-09
forum: Apple PPC Users
---

### Post by old_mac_jeffle on 2005-06-09
Does the default 2.6 kernel for PPC include the MOL module?

---

### Post by chascon on 2005-06-10
[QUOTE=][/QUOTE]
 what does lsmod say?

---

### Post by Ptero-4 on 2005-06-12
[QUOTE=chascon]what does lsmod say?[/QUOTE]
 no, the 2.6 kernel doesn't have those modules. Fortunatelly I have compiled and submitted the modules for both the warty and hoary stock kernels, Peter Van Zaanen has them in his website at [www.petrvz.net/~pvz/kmods](www.petrvz.net/~pvz/kmods).

Hope this helps with your issue.

---

### Post by old_mac_jeffle on 2005-06-13
Ptero-4, thank you for the informative post.

Chascon, do you get paid to post flames? It seems like a waste of time otherwise. :)

---

### Post by chascon on 2005-06-16
> Does the default 2.6 kernel for PPC include the MOL module?
Seems you're heated over the fact that my comment makes you aware of the obvious.  If you know the answer (that the modules are not included), why even ask in the first place?  Instead, why not ask where you can get the modules, rather than waste our time asking a question to which you already know the answer.

Read "How To Ask Questions The Smart Way"
[http://www.catb.org/~esr/faqs/smart-questions.html#answers](http://www.catb.org/~esr/faqs/smart-questions.html#answers)

---

### Post by tread on 2005-06-16
> If you know the answer (that the modules are not included), why even ask in the first place?  
I don't quite understand how you conclude that he knows modules are not included.

> Instead, why not ask where you can get the modules, rather than waste our time asking a question to which you already know the answer. 
If it is a waste of your time, don't answer it.

---

### Post by chascon on 2005-06-17
> I don't quite understand how you conclude that he knows modules are not included.
The fact that he tells me that running lsmod is a waste of time (doesn't report on what it outputs), and that my telling him is also a waste of time.

As far as answering a post that is a waste of time, I didn't say I answered it knowing it was a waste of my time, but after the fact.
And this is getting OT.

---

### Post by zxee on 2005-06-17
Since when does asking "what does lsmod say?" constitute flaming?
Beating up on chascon is like the orginal question-a waste of time.

---

### Post by tread on 2005-06-17
I didn't say he flamed. In my opinion, he could have been more polite, besides, looking repeatedly at the first post I still do not understand his comment.

1. lsmod may not (would not) be obvious to a newbie.
2. The original poster asks if the modules are included, does not say anything about knowing if they are not. So
> f you know the answer (that the modules are not included), why even ask in the first place? 
doesn't make any sense to me.
3. > Read "How To Ask Questions The Smart Way" 
If someone said that to me, I would consider it rude.
4. > The fact that he tells me that running lsmod is a waste of time (doesn't report on what it outputs), and that my telling him is also a waste of time. He does no such thing, and does not report the result of lsmod because his question has already been answered.
5. Yes, it is getting OT, I consider it worth the time and effort spent. I have had experience with rude know-it-all pros when I initially started learning Linux and it is the biggest turnoff possible. I would rather people had a better experience with Ubuntu and Ubuntu forums, after Ubuntu means "humanity to others"
6. Does that answer your question?

Oh, and I am not beating up on him .. I would have no right to anyway.

---

### Post by chascon on 2005-06-19
Who says he was such a newbie?  Regardless of experience, the ordinary cost effective manner is to take he advice, and search on how to apply it if does not know.  Thus, read some HowTos on how to pass lsmod.
From the link:
"If you don't understand...

If you don't understand the answer, do not immediately bounce back a demand for clarification. Use the same tools that you used to try and answer your original question (manuals, FAQs, the Web, skilled friends) to understand the answer. Then, if you still need to ask for clarification, exhibit what you have learned."


> Quote:
Read "How To Ask Questions The Smart Way"
If someone said that to me, I would consider it rude.
Again fron the article:
"Dealing with rudeness

Much of what looks like rudeness in hacker circles is not intended to give offence. Rather, it's the product of the direct, cut-through-the-bullshit communications style that is natural to people who are more concerned about solving problems than making others feel warm and fuzzy.

When you perceive rudeness, try to react calmly. If someone is really acting out, it is very likely that a senior person on the list or newsgroup or forum will call him or her on it. If that doesn't happen and you lose your temper, it is likely that the person you lose it at was behaving within the hacker community's norms and you will be considered at fault. This will hurt your chances of getting the information or help you want."

"Before You Ask

Before asking a technical question by email, or in a newsgroup, or on a website chat board, do the following:

   1.

      Try to find an answer by searching the Web.
   2.

      Try to find an answer by reading the manual.
   3.

      Try to find an answer by reading a FAQ.
   4.

      Try to find an answer by inspection or experimentation.
   5.

      Try to find an answer by asking a skilled friend.
   6.

      If you are a programmer, try to find an answer by reading the source code.

When you ask your question, display the fact that you have done these things first; this will help establish that you're not being a lazy sponge and wasting people's time. Better yet, display what you have learned from doing these things. We like answering questions for people who have demonstrated that they can learn from the answers."

and my favorite:
"Never assume you are entitled to an answer. You are not; you aren't, after all, paying for the service. You will earn an answer, if you earn it, by asking a question that is substantial, interesting, and thought-provoking — one that implicitly contributes to the experience of the community rather than merely passively demanding knowledge from others."

and remember:
"On the other hand, making it clear that you are able and willing to help in the process of developing the solution is a very good start. “Would someone provide a pointer?”, “What is my example missing?” and “What site should I have checked?” are more likely to get answered than “Please post the exact procedure I should use.” because you're making it clear that you're truly willing to complete the process if someone can simply point you in the right direction."

"> 2. The original poster asks if the modules are included, does not say anything about knowing if they are not. So
Quote:
f you know the answer (that the modules are not included), why even ask in the first place?

doesn't make any sense to me.

I can only see two posible scenarios, one he does not know the output of lsmod, in which case he should do research on how to implement it, and the other interpretation is that he seems to know that lsmod does not result in productve info because he complains about my suggesting 'lsmod'.  In either case, he is lacking netiquete, thus the article.  I'm not here to hold people by the hand.  I don't get paid for that.  There are OSes that offer phone assistance if you want to held.  Heck ubuntu might offer that serivce, at least I think they do to coporations (in which case you shouldn't be posting here).  Remember no one here is paid, thus us posters don't owe anyone a 'held by the hand HowTos', nor should the original poster think we do.

Learn to play according to the community's rules.

---

### Post by chascon on 2005-06-19
[QUOTE=][/QUOTE]
 but I think this applies best:
"Prune pointless queries

Resist the temptation to close your request for help with semantically-null questions like “Can anyone help me?” or “Is there an answer?” First: if you've written your problem description halfway competently, such tacked-on questions are at best superfluous. Second: because they are superfluous, hackers find them annoying — and are likely to return logically impeccable but dismissive answers like “Yes, you can be helped” and “No, there is no help for you ... ""
[http://www.catb.org/~esr/faqs/smart-questions.html#answers](http://www.catb.org/~esr/faqs/smart-questions.html#answers)

---

### Post by tread on 2005-06-19
I stand by what I said, I would and do consider some of your style of replying rude.

I never said you should hand-hold someone through the entire solution, but keeping your comments polite and friendly just takes an additional 20-30 seconds.

Its a matter of manners really, but I can see that we will never agree on this point. Lets agree to disagree here and let it go at that.

---

### Post by Flying Llama on 2005-06-19
[QUOTE=Ptero-4]no, the 2.6 kernel doesn't have those modules. Fortunatelly I have compiled and submitted the modules for both the warty and hoary stock kernels, Peter Van Zaanen has them in his website at [www.petrvz.net/~pvz/kmods](www.petrvz.net/~pvz/kmods).

Hope this helps with your issue.[/QUOTE]

How do I go about installing these modules? (I'm quite a newbie, sorry  :smile: )
And let's stop this flamewar, please?  :roll: 

llama

---

### Post by chascon on 2005-06-19
I haven't tried for some time but this should be use full:
[https://wiki.ubuntu.com/MacOnLinuxHowto?highlight=%28on%29%7C%28mac%29%7C%28linux%29](https://wiki.ubuntu.com/MacOnLinuxHowto?highlight=%28on%29%7C%28mac%29%7C%28linux%29)

or just go to wiki at the top of the forums page and do a search for mac on linux.

---

### Post by Flying Llama on 2005-06-19
[QUOTE=chascon]I haven't tried for some time but this should be use full:
[https://wiki.ubuntu.com/MacOnLinuxHowto?highlight=%28on%29%7C%28mac%29%7C%28linux%29]("https://wiki.ubuntu.com/MacOnLinuxHowto?highlight=%28on%29%7C%28mac%29%7C%28linux%29")

or just go to wiki at the top of the forums page and do a search for mac on linux.[/QUOTE]

Thanks for the link, only problem is I cant connect my iBook to the internet with Ubuntu ([Link]("http://ubuntuforums.org/showthread.php?t=42821")). I downloaded the modules archive linked at the beginning of this thread, and brought them to my iBook using my iMac (what i'm typig this on) and a usb flash drive. How do I install it without the internet? (Although the best and most long-term solution would be for me to get Ubuntu connected to the net:wink: )
Anyway thanks,

llama :)

---

### Post by tread on 2005-06-19
If you are saying you can't apt-get, you can download the packages and install them with:

sudo dpkg -i filename.deb

and then continue with the instructions.

---

### Post by Flying Llama on 2005-06-19
[QUOTE=tread]If you are saying you can't apt-get, you can download the packages and install them with:

sudo dpkg -i filename.deb

and then continue with the instructions.[/QUOTE]

Cool thanks.

llama :)

---

