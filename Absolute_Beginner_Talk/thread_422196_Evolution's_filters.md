---
title: "Evolution's filters"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by e6626550w on 2007-04-24
I simply can't get Evolution's filter system to work worth a damn and am getting sick of trying. My question is, is there a known defect in this part of their program? 

I've had no problem in the past setting up filters in either Pegasus  and Eudora ... simple things like color each email from various mailing list a certain color, and then after reading putting them into the appropriate folder and the same on sent mail. 

However with Evolution, nothing seems to work as it should. Before I waste any more time, I would appreciate it if someone would tell me that it is either me or the program. 

Tbird's filter system is rather primitive, but unless I solve this Evolution thing I'll have to use it and I'm way, way off of being enough of a geek to use Mutt ( although I have been able to send and receive mail using it, but it is a long ways off of being really useful as of right now.) ;-)

thanks,
Eileen...

---

### Post by robertpolson on 2007-04-25
"Tbird's filter system is rather primitive"

Have you tried Thunderbird 2.0 ?

I think they have some really good filters. Folders, tags, whatever you need.

---

### Post by e6626550w on 2007-04-25
> **robertpolson said:**
> "Tbird's filter system is rather primitive"

Have you tried Thunderbird 2.0 ?

I think they have some really good filters. Folders, tags, whatever you need.

That wasn't my question, it was whether Evolution's filters work or not? I seem to find some reports from googling that they don't, but nothing definitive. I was hoping that someone here who actually uses this client would be able to give me an answer based on their experience with the program. They either don't or I'm making some stupid mistakes and consistently overlooking them. 

No I haven't tried Tbird 2. I read the writeup on it and there was no mention of improved filtering. 

Eileen....

---

### Post by scanez on 2007-04-25
I've never had a problem with Evolution's filters. Perhaps you're wanting to do something that hasn't been implemented, but to answer your question, yes, they do work.

---

### Post by e6626550w on 2007-04-26
> **scanez said:**
> I've never had a problem with Evolution's filters. Perhaps you're wanting to do something that hasn't been implemented, but to answer your question, yes, they do work.

Thanks,

I'll go back now and try again to find where the program considers me to be illogical. 

Eileen...

---

### Post by jtuchscherer on 2007-07-13
Hi there,

I don't know if this gives you some comfort, but filters aren't working for me, either.
I am using evolution in connection with a MS Exchange server for my business mails and evolution is pretty persistent in not filtering my emails.

(Interesting part: I created the filter in evolution and it didn't work. Rebooted into windows and looking at Outlook. I was surprised to see, that Outlook filtered my emails using the filter I just created in evolution. Never thought, this would work :-) )

---

### Post by jtuchscherer on 2007-07-17
I need to correct myself.
Evolutuion does filter the messages. I oversaw a tiny checkbox in the mailbox settings.
Now it filters alright.

---

### Post by morganpatrick on 2008-02-27
Hi everyone,

I think I have a solution to this problem.

When you add a rule under message filters, there's a dropdown that says, 

"find items:"

 and the dropdown defaults to 

**"if all criteria are met"**

This means that if you add everyone from your office to that rule and have their emails move to the 'work' folder, the filter is only going to work if the sender's name contains Mark AND Brenda AND Rajeev AND Lou AND Dotty AND Mary AND Paul AND Lee AND Tony AND Felipe AND AND AND....

This is not a good default, because when would anyone want to set a rule where the subject, sender, etc contains or is a number of different things? I don't know if this should be considered a bug, but anyway, if you change this dropdown to say:

"If ANY criteria are met"

Then the rules should work. If you've imported your rules from Outlook or Thunderbird, even if they sorted with ANY before, they will now default to try to sort by ALL criteria.

I hope this solves people's problems.

---

