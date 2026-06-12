---
title: "MSN Messenger: I appear offline!"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by Dbugger on 2008-03-05
Help please! What the hell is wrong? 95% of my contacts see me offline and I'm NOT!

It doesnt matter if I use Pidging, aMSN, or even in eBuddy.com! Everyone sees me offline!

Please help!

---

### Post by Joeb454 on 2008-03-05
Perhaps its just the MSN Service that is having issues? :)

---

### Post by Crafty Kisses on 2008-03-05
> **Dbugger said:**
> Help please! What the hell is wrong? 95% of my contacts see me offline and I'm NOT!

It doesnt matter if I use Pidging, aMSN, or even in eBuddy.com! Everyone sees me offline!

Please help!

Are you appearing "Invisible?"

---

### Post by Takuhari on 2008-03-05
did you block 95% of your kontacts?..
did they block you?

---

### Post by AmericanYellow on 2008-03-05
I had this problem quite a while ago. My best friend always appeared offline so I couldn't chat with him unless he started the conversation. I tried everything. I even spoke to Live Services Tech Support. They said that there was nothing wrong on their end and I realized that I had this problem only when using Ubuntu.

So I removed every IM and made sure that my firewall wasn't blocking important ports needed. Eventually everything started working. Also, if you have recently installed anything, it may have caused some conflict.

I have to ask though, did this problem first result when using Pidgin??

---

### Post by iHenry on 2008-03-27
Same problem here.... :S ..


With all the IM programs Kopete, Pidgin, amsn, Kmess....  I'm always offline to my contacts.... the only way to talk with a contact is when i start the chat or if I block it and then unblock it....

Using Windows everything works....

I don't have a firewall, I am VISIBLE, I don't have the contacts blocked....

this is my iptable

 sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


Could be a problem with my account.?

---

### Post by Confuzius on 2008-03-27
When I was using Emesene my friends told me that they could see me, but would get a non-responding user is unavailably type of message if they messaged me first.  If I started the conversation there wouldn't be a problem, but they couldn't start one.

aMsn seems to be working again, but Emesene was much nicer to use.

---

### Post by menkhaf on 2008-04-24
I know the thread is 3 weeks old, but I have the exact same problems, and wanted to share my findings.

For me, it started a few weeks ago. I thought it was a problem with Pidgin/libpurple, but after updating to the newest version of Pidgin, nothing happened; it still didn't always work.

I've tried logging in with Windows Live Messenger, and to my surprise, it had the same problems.

When I log on, most of the time I can't see anyone but myself online. Some times a few other people appear online and shows up in the list.
If people initiate a chat with me, it pops up instantly, but since Pidgin doesn't support server-side offline messages as Windows Live Messenger does, I can't reply -- it just gets saved as a buddy pounce.

Sometimes logging out and back in works, but it is a rarity.

If anyone else has these problems, please write back in this thread with descriptions or solutions.


/Menkhaf


Search keywords: MSN live messenger offline pidgin appear problem bug
(because we might not be the only ones with this problem..)

---

### Post by Joeb454 on 2008-04-25
You can add a couple of those to the "Tags" just above the quick reply box :)

And you may want to try aMSN, it works fine for me, I've never had any issues with it :)

---

### Post by abhiroopb on 2008-04-28
Hacing a similar type of problem, basically if a buddy "appears" offline (as they can on msn), then I just see an offline person chatting with me, and my chats just get saved as future buddy pounces, without the ability for me to actually reply!

---

### Post by sbubba on 2008-05-03
ad so.. I've the same problem! also using amsn :(
is there a solution?

---

### Post by mattheiw on 2008-06-30
For Pidgin users, if you have the "Offline Message Emulation" plugin enabled, try disabling it. "Offline Message Emulation" uses buddy pounces to emulate Windows Live Messenger's offline message capabilities. It will be triggered even if your buddy is only "appearing" offline.

Once disabled you should be able to chat with contacts "appearing" offline... but only if they started the conversation.

---

### Post by Dbugger on 2008-07-01
Wow, Old post, but since I was the one to open it, I will say my advice:

> "eMeSeNe" is the only program where this problem doesnt present. Use it.

Glad to help ;)

---

### Post by Tiftof on 2008-07-13
Check this thread: [http://ubuntuforums.org/showthread.php?t=583408&page=7](http://ubuntuforums.org/showthread.php?t=583408&page=7)

I was having the same problem and I was convinced it was an error at the MSN Servers and somehow the Messenger support team fixed it. I advice you to contact the support team and have some patience.

---

