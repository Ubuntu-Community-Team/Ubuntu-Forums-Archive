---
title: "Pixel, an alternative to GIMP?"
date: 2007-05-19
forum: Art &amp; Design
---

### Post by the lemming on 2007-05-19
Anybody seen or heard of Pixel?

[http://www.linux.com/article.pl?sid=05/12/06/1828230](http://www.linux.com/article.pl?sid=05/12/06/1828230)

I have a large photo collection and want some way to mess around with them now that I have discovered Linux.

Cheers

---

### Post by foresth on 2007-05-19
There's been many threads about Pixel on this forum.

I am a big fan of this project.

---

### Post by the lemming on 2007-05-19
> **foresth said:**
> There's been many threads about Pixel on this forum.

I am a big fan of this project.

Does that mean that it is worth buying a copy?

---

### Post by brian j on 2007-05-19
In my honest opinion, Not really worth buying. I downloaded a copy of pixel some time ago, and within 5 minutes took it off.

---

### Post by ricrac on 2007-05-19
Downloaded and installed on Ubuntu 7.04 with Ubuntu studio metapackages applied
pixeldemo_1.0.560-1_i386.deb

I had to symlink a couple libs...  
sudo ln -s /usr/lib/libIlmImf.so.2.0.2 /usr/lib/libIlmImf.so
sudo ln -s /usr/lib/libjasper-1.701.so.1.0.0 /usr/lib/libjasper.so

Nice interface
Higher latency right now for tools than gimp, xara, or cinepaint
No wacom support yet on linux
Redraw problems using nvidia drivers, especially with eraser, anything merge or delete.  Adding opaque is solid in tools I tried.
Nag screen and watermark for demo version
Help, system info crashed the app.
An unhandled exception occurred at $0821D3F1 :
EAccessViolation : Access violation
  $0821D3F1
  $0821C839
  $080A2167
  $080A2FD1
  $080A3197
  $0821C67A
  $0821E2FF
  $0816B0D8
  $0815D2EE
  $0804E640

Has HDR support, that's a plus, single window interface that some people prefer. 
What works looks good, maybe in a while,  or on SkyOS, what appears to be the developers main platform. Latest build version available only in SkyOS.
[http://www.skyos.org/](http://www.skyos.org/)

** Just a note.  I installed pixeldemo-1.0.560-linux.i386.tar.gz generic linux build on mandriva 2007.1 and got better results.  Will try generic build  on Ubuntu later and update.

---

### Post by maruchan on 2007-05-20
I own Pixel, and I have to say at this point I can't really recommend it. I used it for a few months after I bought it and then I realized that there was a lot of crashing behavior, and it just wasn't stable enough to base my professional work on.

Contrast this with GIMP - I've been using nothing but development versions and I almost never see crashing behavior. Sure there isn't exact feature parity, but I don't really miss anything I had in Pixel, especially now that we have Krita and other cool imaging software.

Looking forward to following Pixel's development, though.

---

### Post by ricrac on 2007-05-20
Sorry to digress but,
If you do production work don't forget to look at nip2.  Batch oriented spreadsheet like interface.
I find it a useful teaching tool for image processing productivity.
No comparison if you have hundreds or thousands of files to process.

Many people flounder in an interface, "what should I do next", nip2 will help to focus on the workflow for better habits when using a full gui editor.

---

### Post by hikaricore on 2007-05-20
Ugghhh last time someone posted about pixel it turned into a 10+ page argument about free vs. commercial software.  lol

---

### Post by P_Badger on 2007-05-21
I'd recommend staying away from Pixel, I've found it isn't capable of doing the *simplest* job without crashing. On top of that, the truly sad state it's in is the result of over ten years of programming, and it's still only at beta 6.

I've used Gimp unstable branch since forever, and don't even have crashing issues with it.

---

### Post by rejser on 2007-05-21
unfortunually I also have to agree with prior speakers. When it works I really like it. Smart program, really usable. But it crashes allot, and worse, feels like random crashes.

---

### Post by mech7 on 2007-05-21
also if you look in the forum most users seem to be pretty upset about that there where claims when releasing new version but never came etc.. no reactions it's a one man band so it could take a very long time before this app becomes mature.

---

### Post by P_Badger on 2007-05-21
> **mech7 said:**
> also if you look in the forum most users seem to be pretty upset about that there where claims when releasing new version but never came etc.. no reactions it's a one man band so it could take a very long time before this app becomes mature.

Long story short, he's been promising beta 7 since June of last year. He's constantly failed to release it, even, (in my opinion), lying about having given "beta testers" access to beta 7, and has now just recently given some line about how he's not releasing beta 7 at all, but going to jump directly to beta 8. Apparently he "added more features" during the writing of beta 7, etc, which was something he wasn't going to do.

---

### Post by zAo on 2007-05-23
To cut the story short: why didn't they go opensource? Why?

I really miss Photoshop (Lightroom), but cum'on: Pixel aint that good.

---

### Post by !nkubus on 2007-05-24
If this go open source one day I must say that gimp is in trouble. Unfortunately it won't happen anytime soon.

---

### Post by Aetherius on 2007-06-05
He's got that basis of a well developed, production ready piece of software... however, given that it is the love child of one man alone, it is ONLY a basis.

If someday he sees the light and sets it free, I can see many many developers jumping on board and within a few short months we could have a very viable production-level photoshop rival.

---

### Post by Incie83 on 2007-07-12
First off: I'm glad to see that this thread hasn't (yet) turned into a completely irrelevant 'HEY I DON'T USE PIXEL BUT HERE'S MY OPINION ON THE GIMP, OPEN SOURCE IN GENERAL AND YO MAMA' yelling contest, I hope it stays that way. What we have here is a very promising project and a lack of balanced (or Ubuntu-based) reviews and opinions.

I've had an experience similar to those of previous posters, and I have to conclude that the current Beta version is highly unstable, too unstable for my liking (running on Feisty, just installed the .deb package from the Pixel website). Having said that, for web designers/developers like me, Pixel is an excellent alternative to the GIMP in terms of lay-out and features (personal preferences aside, it's safe to assume that a significant proportion of Ubuntu users would agree with me and would even purchase the product).

Giving the developer the benefit of the doubt on the whole let's-skip-a-beta-version issue, let's hope the next beta version will be released soon and offer more stability. Let's also hope that the developer comes to realise that flying solo on such an ambitious project is not necessarily the best approach. For now, I won't spend money on a license until I try a beta version that doesn't crash every 10 minutes.

---

### Post by Rohen on 2007-07-13
If we have to pay for it... then aren't we going against the whole open source software movement?  I wouldn't touch it unless it went open source.  I am however, wanting to reaplce GIMP.  I hate the lack of user interface usability.

:(

---

### Post by qamelian on 2007-07-13
> **Rohen said:**
> If we have to pay for it... then aren't we going against the whole open source software movement?  I wouldn't touch it unless it went open source.  I am however, wanting to reaplce GIMP.  I hate the lack of user interface usability.

:(

There is nothing that says free / open source software must be free of charge. They could release the source code under an appropriate open source license and still be entitled to charge for the product, support etc. 

My problem with Pixel has less to do with the fact that it is proprietary and more to do with the fact that I actually prefer the GIMP interface. The MDI model used by the GIMP makes it easier to configure a workspace that is comfortable for me and enhances usability. I could use Pixel, but I would never be comfortable with the interface. It reminds me too much of Photoshop which I also found clumsy to use, even though I did use it for 6 years before discovering GIMP.

---

### Post by Rohen on 2007-07-13
> **qamelian said:**
> There is nothing that says free / open source software must be free of charge. They could release the source code under an appropriate open source license and still be entitled to charge for the product, support etc. 

hmmm... if that's the case, then I don't know much useful software that does that.  Thanks for letting me know.

---

### Post by kadath on 2007-07-13
Pixel is an awesome project marred by lack of communication between the developer (Pavel) and his paying users. The amount of delays and broken promises is reaching a crescendo and I feel like if Pavel doesn't make a new beta release very soon, many people are just going to stop waiting for Pixel.

The current beta (6) shows tons of promise but it is *unusable*. The amount of bugs truly make it a beta, and I fear that we're nowhere closer to a stable 1.0 release than we were a year or two ago. I respect Pavel for the amount of time and work he's put into Pixel, but unless he gets some help coding this thing, development will always proceed at a snail's pace.

As for Pixel being closed source and costing money: Suck it up. Specialized apps cost money, and they often cost *a lot* of money. No one complains that Maya for Linux costs as much as a used car and is closed source. Why? Because it's a specialized app that professionals are willing to pay for and support the company that develops it. It's obvious that GIMP isn't going to become a true Photoshop replacement on Linux, but Pixel could very well. Pavel deserves to be paid for his efforts. Where the GIMP devs have failed, he is succeeding, albeit at a very slow pace.

Despite this, I still stand by my caveat: If money's tight, wait till the end of the year before you shell out money for Pixel. Pixel has come a long way, but it's been almost a year since the last beta release. If we don't see another by the end of 2007, the project might as well be considered dead.

---

### Post by Half-Left on 2007-07-13
> **kadath said:**
> Pixel is an awesome project marred by lack of communication between the developer (Pavel) and his paying users. The amount of delays and broken promises is reaching a crescendo and I feel like if Pavel doesn't make a new beta release very soon, many people are just going to stop waiting for Pixel.

The current beta (6) shows tons of promise but it is *unusable*. The amount of bugs truly make it a beta, and I fear that we're nowhere closer to a stable 1.0 release than we were a year or two ago. I respect Pavel for the amount of time and work he's put into Pixel, but unless he gets some help coding this thing, development will always proceed at a snail's pace.

As for Pixel being closed source and costing money: Suck it up. Specialized apps cost money, and they often cost *a lot* of money. No one complains that Maya for Linux costs as much as a used car and is closed source. Why? Because it's a specialized app that professionals are willing to pay for and support the company that develops it. It's obvious that GIMP isn't going to become a true Photoshop replacement on Linux, but Pixel could very well. Pavel deserves to be paid for his efforts. Where the GIMP devs have failed, he is succeeding, albeit at a very slow pace.

Despite this, I still stand by my caveat: If money's tight, wait till the end of the year before you shell out money for Pixel. Pixel has come a long way, but it's been almost a year since the last beta release. If we don't see another by the end of 2007, the project might as well be considered dead.

The GIMP is not a photoshop replacement for starters, everyone just thinks it is because it's the nearest thing. Pixel is pretty much a clone of PS right down to it's UI, this is all worthless if the program doesn't run proper or is not stable.

People in OSS dont mind paying if it's a good product but Pixel is far from it, in the real terms the development cost for it must have been huge, if you cannot get it stable at this point then you never will.

Also Adobe have patents on the layout of PS, so if Pixel got popular i'd bet adobe would be suing, people really should know better than to directly copy things like this.

---

### Post by kadath on 2007-07-13
> **Half-Left said:**
> The GIMP is not a photoshop replacement for starters, everyone just thinks it is because it's the nearest thing. Pixel is pretty much a clone of PS right down to it's UI, this is all worthless if the program doesn't run proper or is not stable.

People in OSS dont mind paying if it's a good product but Pixel is far from it, in the real terms the development cost for it must have been huge, if you cannot get it stable at this point then you never will.

Also Adobe have patents on the layout of PS, so if Pixel got popular i'd bet adobe would be suing, people really should know better than to directly copy things like this.

I know GIMP isn't supposed to be a PS replacement, but I'm sure you're aware that many Linux users tout it as being so? Even most "open source equivalent" sites list GIMP as being the Linux equivalent of PS. It's a lie and it harms people's view of Linux and open source software.

As far as Pixel's stability goes, I already said that it's buggy as hell. This is why I'm frustrated with its slow-as-molasses development. Pavel *really* needs to get help ASAP, or his project is over with. And that's what makes it a shame, since it's come this far.

As far as Pixel's layout goes, I don't think Pavel has to worry about Adobe suing him. There are many other graphics apps with Photoshop-like layouts, and Adobe doesn't seem to care about them. Pixel won't ever be as popular as Photoshop is, mostly because most Windows users will simply continue to pirate PS instead of buying Pixel.

---

### Post by smartboyathome on 2007-07-13
I would use it if it were stable. But I can't program (as of yet) so I would be no help developing. I would like to see this project suceed, though!

---

### Post by Half-Left on 2007-07-13
> **kadath said:**
> I know GIMP isn't supposed to be a PS replacement, but I'm sure you're aware that many Linux users tout it as being so? Even most "open source equivalent" sites list GIMP as being the Linux equivalent of PS. It's a lie and it harms people's view of Linux and open source software.

As far as Pixel's stability goes, I already said that it's buggy as hell. This is why I'm frustrated with its slow-as-molasses development. Pavel *really* needs to get help ASAP, or his project is over with. And that's what makes it a shame, since it's come this far.

As far as Pixel's layout goes, I don't think Pavel has to worry about Adobe suing him. There are many other graphics apps with Photoshop-like layouts, and Adobe doesn't seem to care about them. Pixel won't ever be as popular as Photoshop is, mostly because most Windows users will simply continue to pirate PS instead of buying Pixel.

The GIMP is classed as a equivalent because it's a image editor like Photoshop. By the way I hate the demo watermarks he put in, even Adobe give fully functional 30 days demos of CS3, he's just going the wrong way about it.

---

### Post by rsambuca on 2007-07-13
> **kadath said:**
> Pixel is an awesome project marred by lack of communication between the developer (Pavel) and his paying users. The amount of delays and broken promises is reaching a crescendo and I feel like if Pavel doesn't make a new beta release very soon, many people are just going to stop waiting for Pixel.

The current beta (6) shows tons of promise but it is *unusable*. The amount of bugs truly make it a beta, and I fear that we're nowhere closer to a stable 1.0 release than we were a year or two ago. I respect Pavel for the amount of time and work he's put into Pixel, but unless he gets some help coding this thing, development will always proceed at a snail's pace.

As for Pixel being closed source and costing money: Suck it up. Specialized apps cost money, and they often cost *a lot* of money. No one complains that Maya for Linux costs as much as a used car and is closed source. Why? Because it's a specialized app that professionals are willing to pay for and support the company that develops it. It's obvious that GIMP isn't going to become a true Photoshop replacement on Linux, but Pixel could very well. Pavel deserves to be paid for his efforts. Where the GIMP devs have failed, he is succeeding, albeit at a very slow pace.

Despite this, I still stand by my caveat: If money's tight, wait till the end of the year before you shell out money for Pixel. Pixel has come a long way, but it's been almost a year since the last beta release. If we don't see another by the end of 2007, the project might as well be considered dead.

I have no problem donating or paying developers for products that suit my needs and I can use with reasonable stability.  Unfortunately, as much promise as this project has, I will not be paying for a license anytime soon as there is absolutely no assurances that pixel will be anything more than a POTENTIALLY good piece of software.  I understand that this is obviously the guy's pride and joy, but if he could only step back and look at the project objectively, he would realize that he needs some help with it.  Quite sad really, as it may just become a grandiose waste of his time if he doesn't pick up the pace.

---

