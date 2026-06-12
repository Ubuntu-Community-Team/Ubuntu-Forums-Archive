---
title: "When providing noobie help..."
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-02-23
First, I'm very grateful to all of the forum people who have helped me.

What I would like to suggest is that, when offering help, it would greatly assist my understanding of Linux (in general) and Ubuntu (in particular) if some sort of explanation would accompany the terminal commands I'm supposed to type in.  

With a better understanding of the problem and its solutions I would be better able to help others with similar problems - which would help spread the workload at the beginner forum out a bit.

In other words, I would like to assist noobies who are having problems similar to the ones I've had.  But I first need to understand how the problem I had was caused, and how whatever it was I was instructed to do, fixed it.

---

### Post by Robgould on 2006-02-23
well....when someone takes the time to tell you what to type in the terminal that is just the first step. If you type it in and it works, that is step two. Step three should be you using resources at your disposal to investigate the why. A lot of times these cannot be summed up in a sentence or two.
 
For example if I told you to type:
 
```

chmod -R 777 /etc/somefile

```
 
It would take a long time to explain all the parts of the command in a meaningful way.  Would involve talking about permissions and switches and security.  What all the numbers mean.  Basically a lot of stuff.  
 
By contrast you could do some research on the chmod statement, or linux permissions, and come up with some meaningful reading like [this]("http://forums.fedoraforum.org/attachment.php?attachmentid=5871").
 
I also don't think you should try to explain something to other people based upon something you read on here but don't understand.  Instead, provide a link to the post that helped you.  
 
If you take a few minutes though and do some research you will easily be able to help others.  Ro instance after reading that link above you should be able to carry on a conversation about linux file permissions.  In fact you will know more about it than probably 40% of the people on these forums.  There is a lot more to know about it from there.  See if you can find it.

---

### Post by Xian on 2006-02-23
If a command is given with no explanation there are many resources to get that information yourself. While it would be nice if each such instance met your needs precisely, the great thing about Linux is that the system management requirements and information are so transparent and readily available. 

1. Use the man file. For example, with a 'cp; (copy) command:
$ man cp

2. Search the net.

3. Use online [RESOURCES](http://www.ss64.com/bash/).

4. Research, learn, share.

---

### Post by Iowan on 2006-02-23
From the  forum guidelines:> Elaborate. Walk the user through the procedure -- Remember that this may be the person's first time opening up Synaptic or editing a configuration file. Remember that this is in a forum specially designed for those who need a little extra care. If you don't have the patience to do so, consider allowing someone with the patience to answer the question instead.

That said... consider how many times the same issues come up in the forum.  For example, "I don't have permission to..., how do I get it?"  I'll agree that a simple "Use **sudo**" isn't an adequate explanation, but a complete discourse on **su** vs **sudo**, how to setup the **sudoers** file, what **sudo** does, and why Ubuntu uses **sudo** instead of the normal **root** account for each of the 50-60 times the question is asked might not be the best use of board space (much like my rambling).  Consider asking a specific question about a command and someone will jump at the opportunity to enlighten you.  Just my unsolicited opinion...

---

### Post by echo $USER on 2006-02-23
I bought a used book "pocket guide to the linux terminal" that helps alot for quick references.

---

### Post by Brunellus on 2006-02-23
[QUOTE=Cousindaddy]First, I'm very grateful to all of the forum people who have helped me.

What I would like to suggest is that, when offering help, it would greatly assist my understanding of Linux (in general) and Ubuntu (in particular) if some sort of explanation would accompany the terminal commands I'm supposed to type in.  

With a better understanding of the problem and its solutions I would be better able to help others with similar problems - which would help spread the workload at the beginner forum out a bit.

In other words, I would like to assist noobies who are having problems similar to the ones I've had.  But I first need to understand how the problem I had was caused, and how whatever it was I was instructed to do, fixed it.[/QUOTE]
We use terminal commands because they are quick and, if you can cut and paste (or even copy and transcribe) accurately, there is *zero chance* that our instructions will be misinterpreted.  

As someone else has noted above, some of the commands, while themselves very short, require rather long-winded explanations to *understand*....most of which is not needed for someone who needs a problem fixed *this instant*.  

Reading manual pages is good.  Buying a good book that will talk about some basic shell coammands is even better.

---

### Post by aysiu on 2006-02-23
When giving help, I try my best to put myself in the place of a new user, as I was a new user less than a year ago.

When I had problems, the #1 thing I wanted was my problem solved. Only after that was I concerned about what exactly happened that solved the problem. I can't give long explanations as to what commands mean for *every* command I give.

I have had some new users (especially in the last two weeks, for some strange reason) ask "Okay. I'll try that. What do those commands mean, anyway?" in which case I'm more than happy to explain.

It also doesn't hurt to use Google to find out.

I'm not going to explain all the differences between root and sudo every time I ask someone to use a *sudo* command.

---

### Post by wrtrdood on 2006-02-23
I agree that explanations are beneficial but only to those truly interested in taking the time to learn what they mean.  As stated, there are a lot of questions that fly across the forums and detailed answers require a fair amount of work.

In the case of shell commands, most, if not all are fully documented right where you are.  Even us old SAs have occasion to use the manual and that's exactly what you'll get via the *man* or *info* commands.  Not sure what command might be appropriate?  That's where *appropos* comes in handy.

As for GUI related help; proper explanations for this can be very time consuming.  Quick replies usually create more problems for the end-user and often there are steps left out which add to the confusion.  Truly helpful answers require a great deal of effort and not everyone is up to the task.  That being said, I've seen some excellent posts here that take all that into consideration.

  In most cases it's been my observation that if new users would spend more time searching the forums they might often find the answers they seek.  To be fair, there are many posters that do just that.

Bottom line:  I think a lot of the helpful posts that seem terse to the new user are a result of others not truly reading what was written in the first place.  This tends to leave an atmostphere where those with the knowledge become weary of repeatedly saying the same things every time.

---

### Post by suRoot on 2006-02-23
This is probably one of the more concise cheat sheets I've ever run across...

[http://homepage.powerup.com.au/~squadron/linux_manual.pdf](http://homepage.powerup.com.au/~squadron/linux_manual.pdf)

might be helpful if you don't understand all the commands.

---

### Post by Robgould on 2006-02-23
That is a very nice link suRoot.  I have never seen that before.

---

### Post by aysiu on 2006-02-23
[QUOTE=wrtrdood]
Bottom line:  I think a lot of the helpful posts that seem terse to the new user are a result of others not truly reading what was written in the first place.  This tends to leave an atmostphere where those with the knowledge become weary of repeatedly saying the same things every time.[/QUOTE] Guilty right here. I often don't read the original post carefully enough and just assume it's the same old question and give the same old answer (and tersely). I've got to re-sharpen my reading skills.

---

### Post by suRoot on 2006-02-23
Yeah, it is a nice cheat sheet.  Some of it is outdated, but for the most part it's still fine.

---

