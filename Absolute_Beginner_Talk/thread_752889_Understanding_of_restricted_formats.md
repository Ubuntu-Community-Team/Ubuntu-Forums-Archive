---
title: "Understanding of restricted formats"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by _godbout_ on 2008-04-12
Hi there!

I'm wondering if I understand correctly these stuffs about restricted formats.
So, please tell me if I'm right or wrong. Let's take the mp3 format for example.

If Ubuntu comes directly with mp3 support, would it have to pay for a license?
What about installing the codecs which allow us to play mp3? Do the people who wrote the codec have to pay? What about encoder/decoder?

If I understand well, only people who are building hardware which support by default the restricted format have to pay something? It's still a bit blur to me about the codecs.

---

### Post by Mick8882003 on 2008-04-12
its mainly to protect the writers of the code from legal action...

---

### Post by _godbout_ on 2008-04-12
Argh, I don't understand what you mean, sorry :D
The writers of Ubuntu or the writers of the format?
Which legal action?

---

### Post by ibutho on 2008-04-12
Most restricted formats either require licensing fees or have potential issues with patents. Using them without paying the appropriate licensing fees or permission from the people who own the patents can result in legal action against those that ship the software. This is the reason why most distros prefer not to ship packages that can cause them legal problems (especially those based on the US). Those that give easy access to restricted formats usually host the servers in countries where the laws are not so restrictive as in the US.

---

### Post by _godbout_ on 2008-04-12
Ok, but for example, mp3, everybody is using it right? I assume in US also. I guess that for the end-user, it's same-same. We don't have to pay. 
But for a manufacturer who provide a player which supports mp3, he will have to pay.

Now, what I feel a bit strange, is that the distro doesn't give it (which I really understand) but we can make it available so easily. Do you mean that these codecs that we d/l are not so "legal"? Or they are not legal in the US but elsewhere yes?

---

### Post by chewearn on 2008-04-12
There is plenty of discussion about these issues already in the forum.  Hint hint: google. :smile:

None of us have the power of attorney (I think that's the right term) here to give you the answers you are looking for.  There might be actual lawyers here, but you won't get bulletproof "law" advice.

If your need to know is business related, seek a professional lawyer.

---

### Post by _godbout_ on 2008-04-12
Hey, thanks!

I've looked for explanations already, read the ubuntu blabla etc..., but I'm still not ok with that. There is no link with any business, I just like to understand the why and how :)

Thanks again,
I'll try to look a bit more, and maybe to stop thinking about that.

---

### Post by chewearn on 2008-04-12
Hi, apologies; I re-read my reply #6 and realized it's unhelpful.  To make up for it, here is a recent thread with a lot of discussions on the legal issues.
[http://ubuntuforums.org/showthread.php?t=728031](http://ubuntuforums.org/showthread.php?t=728031)

---

### Post by LaRoza on 2008-04-12
> **_godbout_ said:**
> Hi there!

I'm wondering if I understand correctly these stuffs about restricted formats.
So, please tell me if I'm right or wrong. Let's take the mp3 format for example.

If Ubuntu comes directly with mp3 support, would it have to pay for a license?
What about installing the codecs which allow us to play mp3? Do the people who wrote the codec have to pay? What about encoder/decoder?

If I understand well, only people who are building hardware which support by default the restricted format have to pay something? It's still a bit blur to me about the codecs.

It is mainly a philosophical thing than a legal one IMO.

If you read the Ubuntu philosophy, it states it will only contain free software.

Many distros do contain these codecs and I know of no case where anyone had any sort of legal action because of it.

---

### Post by _godbout_ on 2008-04-13
Thanks a lot all for your answers.
Thanks AstalaVista for the link, I'm gonna have a look.

---

### Post by spydon on 2008-04-13
> **LaRoza said:**
> It is mainly a philosophical thing than a legal one IMO.

If you read the Ubuntu philosophy, it states it will only contain free software.

Many distros do contain these codecs and I know of no case where anyone had any sort of legal action because of it.

Ubuntu doesn't only contain free software, but gobuntu does...
There are some drivers and libraries that are closed or/and restrict the users freedom.

---

### Post by scorp123 on 2008-04-13
> **_godbout_ said:**
>  I'm wondering if I understand correctly these stuffs about restricted formats .... If Ubuntu comes directly with mp3 support, would it have to pay for a license? What about installing the codecs which allow us to play mp3? Do the people who wrote the codec have to pay? What about encoder/decoder?  

> **LaRoza said:**
>  Many distros do contain these codecs and I know of no case where anyone had any sort of legal action because of it. Fraunhofer Institute and Thomson Electronics so far have not enforced their patents against makers of free + open source software. But they **do** and **will** go after **commercial vendors** who distribute MP3 encoders / decoders without proper licensing. Read here:

[http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/Mp3#Licensing_and_patent_issues)

Also, there is a certain confusion over who owns exactly what when it comes to MP3 as several companies claim ownership of various aspects of the patent. In short: It's a legal mess.

So this puts Canonical Inc. --the makers of Ubuntu-- into a difficult position, like most makers of Linux distributions: What are they? A commercial company? One one hand: Yes. They sell support for their Linux distro, so they do make money out of it. Or are they not? Fact is they give Ubuntu away for free ... So are they commercial or not? Would it therefore be legal for Ubuntu to ship with MP3 codecs pre-installed ... or not? It's a risky choice. So as nobody is really keen on having to find out in a lawsuit which of those two aspects is right most if not all Linux vendors which have a company behind (Ubuntu, Novell, Red Hat) avoid distributing MP3 and other problematic codecs or they license them ... which in turn puts them into a questionable position as far as potential GPL violations are concerned, e.g. Linspire: [http://en.wikipedia.org/wiki/Linspire#Criticism](http://en.wikipedia.org/wiki/Linspire#Criticism)

Let's also take "Linux Mint" for comparison: They ship with all the codecs pre-installed. How and why can they do that? Mint is based in Europe where software patents are (still) invalid for the most part: the main developer is in Ireland, the OS is being distributed off servers physically located in Germany. And there is no company behind "Mint", it's a one-man-show by Mint's creator .... And so far this puts Mint in a position where it can slip under the MP3 patent holders' radar screens and not become a target.

The same patents that make it problematic for e.g. Canonical Inc. to include the MP3 codecs in Ubuntu also seem to state that it is OK for anyone to download and/or program MP3 encoders and decoders for as long as the software that is produced in the end is distributed under a free and non-commercial open source license. So by this it (apparently?) is perfectly legal for Linux programmers to write free software that can encode and decode MP3 and it is legal for you and me to manually download the needed pieces to enable the format on our computers if we want to.

I hope this helped ....

---

### Post by _godbout_ on 2008-04-18
> **scorp123 said:**
> ...a lot of interesting things...

I hope this helped ....

Oh man!!! Incredible, this totally explain and answer my questions perfectly. Thanks a lot!
I totally understand now!

Give you a medal :p

---

