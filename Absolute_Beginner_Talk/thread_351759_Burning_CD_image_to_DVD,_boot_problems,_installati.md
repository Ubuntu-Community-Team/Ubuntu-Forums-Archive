---
title: "Burning CD image to DVD, boot problems, installation troubles"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Old Pink on 2007-02-02
[FONT=Verdana][SIZE=2][I]This thread has been started on behalf of a friend, [ryan444123]("http://www.ryan444123.com"), who is having difficulties using Ubuntu, and does not have an active account here.

I am a full time Linux user, and would assist my friend should I have any means of physical interactivity with him, but our friendship is online based and I have offered all the advice I can. 
[/I]
Hi, 

My friend's having a little trouble getting started with Ubuntu. He's burning a CD .iso to a blank DVD, which may be the cause of the problem.

I've checked that he's using an .iso burner, and not just placing a raw .iso on the DVD. 

I've asked what happens when booting from this DVD, and he says "The computer boots, and then nothing happens", but hasn't gone into any detail. 

He's also tried the alternate CD, upon my request, and has found that he's having the same issue here. I've also confirmed that his BIOS knows to boot from the CD, and not the hard drive.

Here's an archive of our conversation:[/SIZE][/FONT][SIZE=2]
> 
**Ryan@forumfinder.net: **good afternoon

**me: **Hi. [IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]

**Ryan@forumfinder.net: **morning here still. [IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]
I haven't talked with you in six months or so.
its amazing.

Sent at 4:51 PM on Friday

**Ryan@forumfinder.net: **you still working with ubuntu?

**me: **Yes. [IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]

Sent at 4:53 PM on Friday

**Ryan@forumfinder.net: **I HATE installing that.,
I have been working for a month and I just am gonna order a CD. 

**me: **Why do you hate installing it?

**Ryan@forumfinder.net: **I have yet to get it to wrok
woirk
work
I am trying to do an alternate install on a windows 98 se running 128 MB ram with a 1.8 ghz processor.

Sent at 4:56 PM on Friday

**Ryan@forumfinder.net: **I don't know what the problem is
Would it be a problem if I burned the CD .iso to a DVD?

Sent at 4:58 PM on Friday

**me: **No idea, to be honset.
*honest.
Can't see why.

**Ryan@forumfinder.net: **I'd have to guess that'd be a problem

**me: **What happens exactly?

**Ryan@forumfinder.net: **Nothing, i boot up the computer and nothing happens.

**me: **Hm.
Does BIOS know to boot from CD?

Sent at 5:03 PM on Friday

**Ryan@forumfinder.net: **yes

**me: **Hm.
Try burning to a CD.
If not, try the installation only CD.

**Ryan@forumfinder.net: **i don't have a cd atm.
i have to go buy some next week i think

**me: **I'll make a thread for you detailing the situation at ubuntuforums, if you wish, and I'll send you a link when you receive some support?

**Ryan@forumfinder.net: **that'd be awesome.

**me: **Could you outline what hardware you're using?

**Ryan@forumfinder.net: **hold on lemme go grab the print out

**me: **OK.
Wait up Ryan
When you burn this DVD
What exactly are you doing?

**Ryan@forumfinder.net: **kk
i am burning a .iso file to a dvd

**me: **Like, when you open the burnt DVD, is there just an .iso file on there?

**Ryan@forumfinder.net: **dvd-r to be exact
hmm no.
thats strange.
I just opened 3 of them and none show the .iso

**me: **They shouldn't.
What are you using to burn the iso?

**Ryan@forumfinder.net: **infran recroder based on prior request in the thread

Sent at 5:16 PM on Friday

**me: **Just wondering...
A common mistake is to burn the raw iso to the DVD root, resulting in an .iso file on a DVD.

**Ryan@forumfinder.net: **LOL
nope i followed the directions on unbuntu

**me: **Haha, OK.

Sent at 5:18 PM on Friday

**Ryan@forumfinder.net: **yep, [IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]
my cpu is using 66% with just firefox open so this is wayy ****** up

**me: **Lol :S

**Ryan@forumfinder.net: **its a dell.

**me: **Oh... have you tried the installation CD?

**Ryan@forumfinder.net: **what can i say

**me: **LOL.

**Ryan@forumfinder.net: **uhmm 
i don't have CD's so no.

**me: **I assume you're using the common Live CD, but some computers don't support it, and require a simple (no GUI) installation CD.
Replace "CD" with "Image" then [IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]

**Ryan@forumfinder.net: ****nods**
I used the "alternative" installation.
[IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]
I figured that out after about the 4th time

**me: **Haha, no luck there either?

**Ryan@forumfinder.net: **nope
 [/SIZE]                                                                                        [FONT=Verdana][SIZE=2]

Basically I'm wondering if the CD image on a DVD-R is a problem.

Hoping for any help, will link to this thread for my friend. 

- Matt[/SIZE][/FONT]

---

### Post by punx45 on 2007-02-02
considering the machine is currently running Win98 with 128MB of ram (despite the 1.8GHz processor :confused: ) I would say the problem is likely the lack of a DVD drive.  Of course, one then has to assume the DVD-R are around for some non-computer related reason.

---

### Post by Old Pink on 2007-02-02
Windows 98 and 128MB of RAM doesn't stop you installing your own DVD reader/writer. 

Or using an external one, for that matter. But I'll ask him, thanks. :)

---

### Post by ryan444 on 2007-02-02
I do have an internal dvd reader/writer it was installed one year ago. I finally was able to resurrect my account, thanks to gmail search.

---

### Post by Kabamaru on 2007-02-17
*Hope this is no longer an issue for your friend - as this is a late response.*

My experience is limited, but it seems to me like your friend may have at least two things to check out:
1) 128mb ram -  my understanding is that this is too little to run an install from a standard Ubuntu CD (or DVD I suppose), although an Alternate CD or Xubuntu (Xubuntu should work as a Live CD, though an installation may require more ram) may work.
2) Md5sum - I'd have your friend make sure his burnt image checks out with regards to [Md5sum]("http://en.wikipedia.org/wiki/Md5sum").  He may have already done this, but it's worth a try.

In direct response to your question regarding burning an image to a DVD instead of a CD:  I don't know.

---

