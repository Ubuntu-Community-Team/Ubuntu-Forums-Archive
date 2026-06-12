---
title: "Mactel Documentation Planning"
date: 2008-11-03
forum: Apple Hardware Users
---

### Post by cyberdork33 on 2008-11-03
> **beauman said:**
> I installed ubuntu on the mac two weeks ago for the first time.
And I can just say, that the pages are a bit confusing.I agree

> **beauman said:**
> You have noticed, that I looked in the wrong wiki.
I did know about the Santa Rosa pages, I found them in the
literature list of an article about installing ubuntu on a mac
book in the german magazine "CT". But I didn't care about it, because
1) its written for gutsy 2) I don't know what Santa Rosa is.
The "Mac geek" in my department didn't knew about it today either.
Well the base MacBook page has a note at the top... "If you own a MacBook of the Santa Rosa generation (v3.1 and v4.1) see [this guide]("https://help.ubuntu.com/community/MacBook_Santa_Rosa")..."


 > **beauman said:**
> The MacBook has this really really great feature to give an unique
hardware identification. So, if anybody refers to a MacBook in a wiki
it should always be "MacBook, + identification string".
Yes, in fact, all Macs have this ability, bit nobody uses it. You can see that I have a link in my signature about properly identifying your Mac and linking to the correct wiki pages. (The "before you post" link).


 > **beauman said:**
> A newbee like me should be able to find the right wiki in just a matter
of seconds. This also means, that the actual page "MacBook ubuntu user documentation" must be renamed.
go for it. Since it is a wiki, you can edit it as well.


 > **beauman said:**
> I also think, sombody how likes to install ubuntu will/should always 
use the latest version. So all wikis should be up-to-date
with the RC comming out.
While that is true, keeping older documentation around can be helpful too, though I think the "main page" needs to be completely up to date.. Kosumi has suggesting creating a new page for each Ubuntu release. You can see this with some of his MacBookAir pages.


 > **beauman said:**
> Please give me some time. I really like to see what you already did
and use it. I also like to discuss everything here. Nobody can do
this alone, because it needs a lot of MacBook owners to report
their experiences.
yes, the more help the better.

---

### Post by cyberdork33 on 2008-11-03
Ok, first for anyone that is planning to create / edit / update wiki pages, 

The pages under "wiki.ubuntu.com" are not for support documentation. That wiki is for Teams and organization. This is where I have placed a bit of "mactel-support" team info.

[https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam)
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

The How-Tos and hardware docs should go in the community help wiki under the URL "help.ubuntu.com/community". This includes the installation guides and such that most users use to install Ubunt on their Mac. Examples:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

Please be sure to place infomation is the correct location so that others can find it easily. Also, if there are any pages in the wrong location, they should be moved and a link placed in the old page.

---

### Post by kosumi68 on 2008-11-03
Inside the community wiki, one can redirect to new pages by keeping a single line in theo old page:
```

#redirect newpagename

```
However, I don't know if this works between wikis.

---

### Post by kosumi68 on 2008-11-03
Cyberdork, it's great that you copied that PPA page over, but many of the links broke and needs fixing... there is a nice feature called 'which pages link to here' to repair such things.

---

### Post by beauman on 2008-11-03
Hi!

What we need, is a meta structure for wikis about ubuntu on intel macs.

It's supposed to lead an owner of such a hardware to the right
wiki page. 

You can find out, what your Macintosh hardware is, by typing
the following command in a terminal:

```
sudo dmidecode| grep Product
```

or

you can look it up under OS X (Apple-> About this Mac -> Details)
[What is the original text in english?]



Ubuntu supports:

MacBook
MacBook Pro
MacBook Air
iMac (Intel based)
Mac mini
Mac Pro (Intel based)

The following hardware versions of these Macintosh products are supported:

MacBook: 
 - 1,1 
 - 2,1
 - 3,1
 - 4,1 
 - 5,1
MacBook Pro:
 - 1,1
 - 2,1
 - 3,1
 - 4,1
 - 5,1 
MacBook Air:
 - 1,1
 - 2,1
iMac:
 - 4,1
 - 5,1
Mac mini:
 - 1,1
 - 2,1
Mac Pro:
 - 1,1
 - 2,1
 - 3,1

(Correct me, if something is missing or wrong)

 I count 19 different hw platforms.

Our wiki should link a user to a wiki of his hardware and the actual 
ubuntu version, which is 8.10 "Intrepid Ibex" at the moment. Also,
we should link to other versions of ubuntu like the LTS version, 
which is 8.04.1 "Hardy Heron".

We should not bother the user with versions of ubuntu, that are not
mentained anymore, like Gutsy and older.

The question is now, if each combination should have it's own wiki named

 Mac Product Name --- Mac Model-Identification --- Ubuntu Version

(short Product/ID/Ubuntu)

or if we should try to merge several version/Model ID's into one wiki.

I would prefere Product/ID/Ubuntu.

We also need mentainers for the 19 hw platforms. These mentainers
should also start beta testing a new ubuntu version and
prepare the page for the upcoming release. If they encounter
any bugs, they should link them (or even post them) to 
launchpad bug-reports, so users can see what the actual status of the
bug is.

If a certain ubuntu version does not support a hardware in a 
satisfying way, we should not recommend this version. Hardy Heron for 
example does not support LAN, wireless and sound on the 
MacBook 4,1.

A wiki for a spezific hardware could contain a table of build-in
hardware and hardware functions which:
   - run out-of-the-box
   - need manual installation
   - will not work at the moment

We should try to think a little bit Mac and not Linux, so
we should not mention the processor name or certain chipsets
in the wiki headline (like penryn and sankta rosa; I searched
for it on the apple site with no relevant results; also the 
Hardware overview of OS X does not mention it either)
Also, your name creation "Mactel" must be explained, before you
use it in a wiki.

We should use all existing wikis that fit into our hardware/ubuntu
matrix, if it's ok for everbody, that we maybe alter the headline
to our naming style or change something else.

The wikis should just serve as the purpose to help a user
improve their installation. "Internal" remarks should be
placed at the end of the wiki or in a mactel support wiki.

All common questions for the Mac side like rEFIt, diskutil or mountig ext3
should be placed in a central wiki. Only if a hardware needs specific
instructions for OS X we put it on the spezific hardware wiki.

We should try to be exact with names and spelling.
It's "MacBook Pro" but "Mac mini". My native language
is german, so correct me whereever you can.

Also, we should think about translating the wikis to other
languages than english.

I like the pictures in the MacBookPro wiki.

Regards,
beauman

---

### Post by kosumi68 on 2008-11-03
beauman, nice post!

Small thing: I have seen examples of iMac8,1.

Big thing: Structure can only be suggested, not enforced. I like your structure idea a lot, and starting work in that direction, talking to the people who maintain the pages, is possible. However, copying all pages somewhere and expecting people to follow is not realistic. It will have to be an organic growth, led by good examples.

That said, I believe there is an opportunity right now, since we currently lack quite a few pages about Intrepid. The new pages can be placed into the structure you propose. The old ones should simply be left alone. It only takes about a week for a new page to become established as the top google page, so linking to the new pages is not really an issue.

---

### Post by freakalad on 2008-11-03
For my MBP SR 3.1 single-boot:

Found Intrepid has some pretty good support for hardware.

There are issues with pommed, but this is probably mostly due to the fact that the original developer has since moved on to bigger & better things.

Found Envy to be the simplest way of dealing with video issues

---

### Post by cyberdork33 on 2008-11-03
> **kosumi68 said:**
> Inside the community wiki, one can redirect to new pages by keeping a single line in theo old page:
```

#redirect newpagename

```However, I don't know if this works between wikis.

Good to know. I was wondering about that. Maybe if you use the entire URL?

> **kosumi68 said:**
> Cyberdork, it's great that you copied that PPA page over, but many of the links broke and needs fixing... there is a nice feature called 'which pages link to here' to repair such things.

ah crap. I did it in a bit of haste today. I usually just put the whole page URL as a link myself so I don't think about it otherwise.
I also made a common page for the iSight.

> **beauman said:**
> iMac:
 - 4,1
 - 5,1
Mac mini:
 - 1,1
 - 2,1
Mac Pro:
 - 1,1
 - 2,1
 - 3,1
I think that the Intel iMacs are versions 4,1 - 8,1 right now

There was at least one PPC Mac Mini, so probably 2,1 and 3,1

Mac Pros have been around forever, so I have no idea what  version they are on... 

There are also Xserves (RackMac). I have no idea on the version numbers for it. We have had a few posts on Xserves in the past.

> **beauman said:**
> Our wiki should link a user to a wiki of his hardware and the actual 
ubuntu version, which is 8.10 "Intrepid Ibex" at the moment. Also,
we should link to other versions of ubuntu like the LTS version, 
which is 8.04.1 "Hardy Heron".

We should not bother the user with versions of ubuntu, that are not
mentained anymore, like Gutsy and older.agreed

> **beauman said:**
> The question is now, if each combination should have it's own wiki named

 Mac Product Name --- Mac Model-Identification --- Ubuntu Version

(short Product/ID/Ubuntu)

or if we should try to merge several version/Model ID's into one wiki.

I would prefere Product/ID/Ubuntu.
I think that each platform and version should have a page definitely, plus maybe an extra for the last LTS release. A lot of hardware is the same for different Macs (the Broadcom WiFi cards are command across many Macs for instance.) These can be put on subpages that can be linked in each of the platform pages. Example:
[https://help.ubuntu.com/community/AppleiSight](https://help.ubuntu.com/community/AppleiSight)

> **beauman said:**
> We also need mentainers for the 19 hw platforms. These mentainers
should also start beta testing a new ubuntu version and
prepare the page for the upcoming release. If they encounter
any bugs, they should link them (or even post them) to 
launchpad bug-reports, so users can see what the actual status of the
bug is. The hard part here will be finding the people to dedicate to making these changes all the time. Linking all bug reports might be a little extreme... maybe there could be a single page under the mactel-support team pages for the bugs. (You can actually reach most of these through the mactel-support pages on launchpad.)

> **beauman said:**
> If a certain ubuntu version does not support a hardware in a 
satisfying way, we should not recommend this version. Hardy Heron for 
example does not support LAN, wireless and sound on the 
MacBook 4,1.IDK. Everyone is going to want to run the latest on the latest. People ran Hardy on MacBookPro4,1. I probably would have too if I had one to run it on. Maybe a warning, but still have the information to do it.

> **beauman said:**
> A wiki for a spezific hardware could contain a table of build-in
hardware and hardware functions which:
   - run out-of-the-box
   - need manual installation
   - will not work at the moment
good organization. I like this approach.

> **beauman said:**
> We should try to think a little bit Mac and not Linux, so
we should not mention the processor name or certain chipsets
in the wiki headline (like penryn and sankta rosa; I searched
for it on the apple site with no relevant results; also the 
Hardware overview of OS X does not mention it either)
Also, your name creation "Mactel" must be explained, before you
use it in a wiki. I agree with that, unfortunately, that is just how people come to recognize things here, and hardly anyone pays attention to the real version number of the machines. The other common method to to identify by release date... i.e. MacBook (Late Oct 2008 )

Mactel is a pretty common term for Intel Macs in general. It was not made up here, but brought here from the Apple Users.

> **beauman said:**
> We should use all existing wikis that fit into our hardware/ubuntu
matrix, if it's ok for everbody, that we maybe alter the headline
to our naming style or change something else.

The wikis should just serve as the purpose to help a user
improve their installation. "Internal" remarks should be
placed at the end of the wiki or in a mactel support wiki.
agree. The existing pages need a bit of cleanup. Also, it is difficult to enforce this on pages that are not "ours". People often get quite offended if you delete things they added to the wiki and really they have every right to put it there just like we do.

> **beauman said:**
> All common questions for the Mac side like rEFIt, diskutil or mountig ext3
should be placed in a central wiki. Only if a hardware needs specific
instructions for OS X we put it on the spezific hardware wiki.
Yes. Basically the base install is the same for every mac. this could be put on a single page and linked at the beginning of each platform page.

> **beauman said:**
> I like the pictures in the MacBookPro wiki.
me too. We have an official "Ubuntu mactel-support" logo too. (It is on the launchpad page).
[https://launchpadlibrarian.net/12033723/appleubuntu_192.png](https://launchpadlibrarian.net/12033723/appleubuntu_192.png)

> **kosumi68 said:**
> Big thing: Structure can only be suggested, not enforced. I like your structure idea a lot, and starting work in that direction, talking to the people who maintain the pages, is possible. However, copying all pages somewhere and expecting people to follow is not realistic. It will have to be an organic growth, led by good examples.

That said, I believe there is an opportunity right now, since we currently lack quite a few pages about Intrepid. The new pages can be placed into the structure you propose. The old ones should simply be left alone. It only takes about a week for a new page to become established as the top google page, so linking to the new pages is not really an issue.

Agree. I think that trying to reorganize the existing information is a good way to do that. Also, we should publish these guidelines on the wiki page as well to show that there is agreement on this, and users are general expected to follow the guidelines.

Leaving the old pages can be confusing though. When you have a page that seems to cover all MacBooks, but then they should really be reading the MacBook4,1 Intrepid page...

I think I am going to request a social group be created too. That will allow there to be "mactel-support members" to exist in the forums.

---

### Post by cyberdork33 on 2008-11-03
Join the mactel-support social group!

We can share pictures and have conversations there.

[http://ubuntuforums.org/group.php?groupid=352](http://ubuntuforums.org/group.php?groupid=352)

---

### Post by beauman on 2008-11-04
Hi! You people are really open to new ideas, that is great! :)

I agree to everything you said.

Especially on identifying a Mac. I spoke to two
Mac fans today. Both knew the realse date of
their hardware, none of them knew the Model-ID.
The release date seems to be more important.

The head line of a wiki could be:

Mac Product Name - (Release Date) -Mac Model-Identification -Ubuntu Version

> **cyberdork33 said:**
> 

I think that the Intel iMacs are versions 4,1 - 8,1 right now

There was at least one PPC Mac Mini, so probably 2,1 and 3,1



I triggered one of the guys to check out the Modell-ID of his Mac mini.
He knew that it's second generation intel. The list of models can we
discuss, when we have created a page.

> **cyberdork33 said:**
>  

I think that each platform and version should have a page definitely, plus maybe an extra for the last LTS release. A lot of hardware is the same for different Macs (the Broadcom WiFi cards are command across many Macs for instance.) These can be put on subpages that can be linked in each of the platform pages. 


Yes, subpages are good, especially it's less work when
things change. The allover hierarchy should not be to deep.
People should not be bothered to much with different hardware
than they have. The wiki of their hardware should be easy and clearly arranged.
We can put several wikis together, if it's the same release date
and Model-ID. Example:

MacBook and MacBook Pro (Release Feb. 2008 ) - 4,1 - Ubuntu 8.10 "Intrepid Ibex"

The hardware should be very close and not differ in more than a couple
points.

> **cyberdork33 said:**
>  
 The hard part here will be finding the people to dedicate to making these changes all the time. 

Let's just try it :) 

> **cyberdork33 said:**
>  
Linking all bug reports might be a little extreme... maybe there could be a single page under the mactel-support team pages for the bugs. (You can actually reach most of these through the mactel-support pages on launchpad.)


Okey dokey

> **cyberdork33 said:**
>  
... Everyone is going to want to run the latest on the latest. People ran Hardy on MacBookPro4,1. I probably would have too if I had one to run it on. Maybe a warning, but still have the information to do it.
 

Yes, ok. We link to the actual and to the LTS release. Since the LTS is for
half a year the actual version, there will always be a wiki anyway.
And if we integrated a table of features that "work out-of-the-box/have to
be installed by hand/ won't work", pleople can decide if the prefere 
long term support over supported features. 

> **cyberdork33 said:**
>  
Mactel is a pretty common term for Intel Macs in general. It was not made up here, but brought here from the Apple Users.
 

If we use the word, we should just introduce it. So that people
don't think it's a special hardware they don't have. 

> **cyberdork33 said:**
>  
The existing pages need a bit of cleanup. 
 

We should talk with the people how wrote the pages. Maybe they
like our idea to find a better structure of the Mac wikis.
Or maybe they permit us to change it a bit.

> **cyberdork33 said:**
>  
Leaving the old pages can be confusing though. When you have a page that seems to cover all MacBooks, but then they should really be reading the MacBook4,1 Intrepid page...
 

Yes. Let's just see. If the structure becomes accepted and people
realize, that we a have clear and concise way of helping users,
they might use it and link it. Maybe a search will show us first then.
Or if the they have found both pages, they might prefere ours, because
it looks more accurate and comprehensive.


Ok. So far, so good.

Let's go for the first step:

What pages do we need?

I would say:

 - the meta wiki that helps/introduces the user to ubuntu on mac
   and helps him find the exact wiki he needs.
 - a page for wiki guide lines and for wiki developers
 - a discussion thread

First we should think a about a name for the meta page.
A question is, if we should mention, that it's just
for Intel. I would not restrict it to Intel,
to have it more common. You never know what's
happening in the future. And maybe someday people like
to add a wiki for ubuntu on PPC.

I would suggest:
  "Ubuntu on Mac" (short is good)
or "Installing And Maintaining Ubuntu On Mac Hardware" 
Some other ideas?


To the wiki about our documentation ideas:
We can call it "Ubuntu Mac Documentation" or whatever,
it's just internal anyway. 

And we can continue this thread for a long time.

If we have agreed on a title for the meta wiki, we
can create it. I then like to write the table of
the different supported hardware platforms (So I get familiar with the
markup language :) )

We can then discuss in detail, what hardware platforms
are supported and when they were released by Apple.

If we have a common sense for our goals, naming conventions
and so on, we can create the development wiki. 

With these three sites, which sketch our idea, 
we can then try to reach other wiki writes
and invite them to join via private messages
our in forums.

So long,
beauman

---

### Post by cyberdork33 on 2008-11-04
> **beauman said:**
> - the meta wiki that helps/introduces the user to ubuntu on mac
   and helps him find the exact wiki he needs.
 - a page for wiki guide lines and for wiki developers
 - a discussion thread
This are already taking shape at 
[https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam)
and it's sub-pages:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)
[https://wiki.ubuntu.com/MactelSupportTeam/PPA](https://wiki.ubuntu.com/MactelSupportTeam/PPA)

We should concentrate on keeping these high-level items here. I think that the "intro to ubutnu on the mac" can go on the base page, and the current mactel-support team "about us" type stuff can go to a sub-page.

We can start the discussion thread type of items in the social group pages, and maybe start a irc channel or something in the future.

> **beauman said:**
> First we should think a about a name for the meta page.
A question is, if we should mention, that it's just
for Intel. I would not restrict it to Intel,
to have it more common. You never know what's
happening in the future. And maybe someday people like
to add a wiki for ubuntu on PPC.I see what you are saying, but the PPC and Intel based platforms are completely different beasts. The only thing I have found in common is the HFS+ filesystem, and the Internal iSight on the last G5 iMacs. Besides that, the PPC communitu already has a large expanse of information out there. We could make a combined "Ubuntu on Mac" page (as you suggested) and just link to Intel and PPC sub areas that are maintained independently.

And we can continue this thread for a long time.

> **beauman said:**
> If we have agreed on a title for the meta wiki, we
can create it. I then like to write the table of
the different supported hardware platforms (So I get familiar with the
markup language :) )I really think we should use what we have already. Feel free to update / edit / modify the existing pages.

> **beauman said:**
> With these three sites, which sketch our idea, 
we can then try to reach other wiki writes
and invite them to join via private messages
our in forums.
sounds good

---

### Post by kosumi68 on 2008-11-04
It's trodding along fine here, it seems :-)

Just a few comments:

I think all pages except the MactelSupport and MactelSupport/PPA should go into the community pages. Also the CommunityHelpPages. We, as a team, own our support and PPA, but we do not own the information about how to install Ubuntu on a Mac - people must be able to edit those pages freely.

Regarding combining several models into one page, I believe that is almost what we have today, and it quickly becomes unclear. One can save keystrokes in other ways, by making sure subparts of the procedures that really are identical are kept on the same subpage.

Cheers!

---

### Post by cyberdork33 on 2008-11-04
> **kosumi68 said:**
> It's trodding along fine here, it seems :-)
here too. :) I just thought that this type of stuff is just a little out-of-scope for this forum, but there really hasn't been a better place for it.

> **kosumi68 said:**
> I think all pages except the MactelSupport and MactelSupport/PPA should go into the community pages. Also the CommunityHelpPages. We, as a team, own our support and PPA, but we do not own the information about how to install Ubuntu on a Mac - people must be able to edit those pages freely.
Agree. We cannot completely control the wiki. However, we can strategically manage the information on them. If someone adds information out-of-place, just move it to be inline with the guidelines without removing it and make a note for the edit.

beauman, since you seem eager to start something and have a plan for the page structure, I suggest that you create a template for the support pages to have as a guideline. That will help us understand what you suggest and allow us to easily create new pages from the template. I suggest it be here:
[https://wiki.ubuntu.com/MactelSupportTeam/HWDocTemplate](https://wiki.ubuntu.com/MactelSupportTeam/HWDocTemplate)

> **kosumi68 said:**
> Regarding combining several models into one page, I believe that is almost what we have today, and it quickly becomes unclear. One can save keystrokes in other ways, by making sure subparts of the procedures that really are identical are kept on the same subpage.
I think it is best to focus the wiki for a single hardware type so that the user doesn't have to discern what part applies, and what part doesn't. Unless the hardware is exactly the same... Like the Mac minis. I think the two models are exactly the same except maybe the processor options available. The aluminum iMacs probably fall into this category too.

---

### Post by kosumi68 on 2008-11-04
Great, thanks for moving the MacBookPro pages over to the community pages! It makes it a lot easier to link between them. And renaming the page will also be easy when we've become concrete regarding the naming convention.

---

### Post by cyberdork33 on 2008-11-04
> **kosumi68 said:**
> Great, thanks for moving the MacBookPro pages over to the community pages! It makes it a lot easier to link between them. And renaming the page will also be easy when we've become concrete regarding the naming convention.

They were misplaced anyway. Support documentation is not supposed to be anywhere but in the community support pages. The wiki.ubuntu.com url is for team wikis.

[quote=https://wiki.ubuntu.com/]Welcome to the Ubuntu Community Team Wiki!
This is THE definitive place for members of the Ubuntu community to discuss ideas and store team-related information.[/quote]

[quote=https://help.ubuntu.com/community/]Community Documentation
Welcome to the community documentation for Ubuntu - created by users just like you![/quote]

---

### Post by beauman on 2008-11-05
Hi!

> **cyberdork33 said:**
> This are already taking shape at 
[https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam)


cyberdork33, [https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam)
may become the main page for our task force. As you explained,
wiki.ubuntu.com is for teams and not focused on helping users.

When I am talking about a meta wiki about installing
and maintaining an ubuntu system on a Mac plattform,
I am talking about a wiki just for users.

It should hide the details behind the sceene.

I try to imagine how a Mac user would act and
think, when he decides to install Ubuntu.

He never cared about what the actual
hardware is he used. That's the Mac philosophy and
also, he never had to care, since everthing is preinstalled
and worked out-of-the-box for him.

Now things change for him a bit. Now he needs a wiki,
because he has to install an OS on his own. Maybe also,
because his webcam might not work without his doing. This
depends on his product, the hardware revision he has
and the version of ubuntu he likes to install and
bring up-to-date.

He would probably google for something like
"mac ubuntu" or maybe "MacBook ubuntu", if he has a MacBook.

One of the first hits might be our "meta wiki" maybe called
"Installing and mainting Ubuntu on a Mac". He will click it,
because it's exactly what he is looking for.
In the first moment he doesn't care who wrote it. 
He won't google for "mactel ubuntu" and maybe the word "Mactel"
might confuse him. Mac user tend more to view their
hardware as a designer peace then a standard Intel laptop.
Otherwise it wouldn't be white :)

So, he reached our "meta wiki". He is just looking
for the information about how to install
ubuntu or how to fix the problem with the broken webcam.

Now we have to explain to him, that he needs to know the exact
hardware version he has, so we can direct him to the right place.
We explain him, that he either has to remember the production
date of his modell, or that he can look it up under OS X
or that he can execute a certain command under ubuntu.

Then he finds a comprehensive table which lists all models and
their respective hw-revisions by production date and model-ID
over the different Ubuntu versions we recommend for him.

He will find his exact model and click the link to the Ubuntu
version he likes best (either the actual or the LTS)
E voila, he made it, to navigate through the jungle of 
wikis that exist at the moment.

This was originally my idea. You guys have extended this idea
a lot, and I really like it! It's cool that you have created
a group for us and that we agreed to act as a team. You are also
much more experienced to the wiki sites of ubuntu. That is
going to help us a lot. And you wrote a lot wikis yourself,
that's also very cool.

Now we should go step-by-step. The first question is, if
we only support Intel mac or just all Mac.
If you say, it's just Intel, then it would be ok for me.
You have the right of older here (because you did that
mac support much longer then me) Personally, I would prefer
to have it common. That leaves us more space for the future.
Of cause we should focus on Intel Macs. That's state of the art.
Somebody who likes to install Ubunutu on an 8 years old PPC,
might be a computer freak anyway and might not need a wiki at all. 
But it's nice and open minded if we have some links at least.
If some day Mac starts using 128Bit processors not coming from Intel,
we just add a new table for this device class. I would place
it all on one site, so the overall hierarchy doesn't become to deep.
In the first step we can just link to a PPC site which we think
fits best. The way of naming wikis and organize them, will be
the same for all processor types.

If we have agreed on this point, we have to find a name
for the "user-interface" of our project.

One point we should think about, how we get it ranked top
at google.

We can then create it and see, how we arrange it. We also
have to discuss, what models are supported and what their 
release date is.

A private note: I am flying to Vienna/Austria tomorrow
until monday, and I can only go online at Starbucks&Co.
So I might not be very active the next days, sorry.

Friendly regards,
beauman

---

### Post by calebio on 2008-11-05
I like this effort and would be happy to help out. My **first comment** is in regards to getting to this new set of pages. When I look for documentation on Ubuntu, I often start at _[www.ubuntu.com](www.ubuntu.com)_, click Community > Help and Information > Documentation and end up _[here]("https://help.ubuntu.com/community/")_.

Then, for my MacBook Pro (or other previous laptops), choosing _[Installation]("https://help.ubuntu.com/community/Installation")_ > Laptops I get to the _[Laptop Testing Team Apple Macintosh]("https://wiki.ubuntu.com/LaptopTestingTeam/Apple_Macintosh")_ page, at which point i get lost and confused, as that is all very hardware-specific and old.

Can that page get linked to the new _[Mactel Support page]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")_, or subsumed by it?

**Second note**, can the _[MacBook Aluminum]("https://help.ubuntu.com/community/MacBook%20Aluminum")_ page be linked from the _[Mactel Support Page]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")_ as a new item for 'MacBookPro5,1'? I see that one is help.ubuntu and the other wiki.ubuntu. Sounds like the latter is out of place:

> **cyberdork33 said:**
> They were misplaced anyway. Support documentation is not supposed to be anywhere but in the community support pages. The wiki.ubuntu.com url is for team wikis.

---

### Post by cyberdork33 on 2008-11-05
> **beauman said:**
> This was originally my idea. You guys have extended this idea
a lot, and I really like it! It's cool that you have created
a group for us and that we agreed to act as a team. You are also
much more experienced to the wiki sites of ubuntu. That is
going to help us a lot. And you wrote a lot wikis yourself,
that's also very cool.
And I think you can use the page here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

to get started with that. It already has the information to identify your mac, and the links to the support pages for each hardware type. As the newer support pages are made those links can be modified to be more in line with the way you suggest.

> **beauman said:**
> Now we should go step-by-step. The first question is, if
we only support Intel mac or just all Mac.
If you say, it's just Intel, then it would be ok for me.
You have the right of older here (because you did that
mac support much longer then me) Personally, I would prefer
to have it common. That leaves us more space for the future.
Of cause we should focus on Intel Macs.
I understand your concern for future growth, but there is no sign of the basic architecture changing anytime soon, and it is good to specify that we are not referring to PowerPC based macs (they have their own problems and issues as it is, they don't need anymore confusion). If there is a change in the future, it will likely be a very different computer (again) and a new "team" or group of skilled individuals will need to pickup support of that hardware (maybe some of the same individuals that are here). Right now, let's just focus on the current state of things, and we can worry about expanding our scope when the need comes.

> **beauman said:**
> Somebody who likes to install Ubunutu on an 8 years old PPC,
might be a computer freak anyway and might not need a wiki at all. 
But it's nice and open minded if we have some links at least.
If some day Mac starts using 128Bit processors not coming from Intel,
we just add a new table for this device class. I would place
it all on one site, so the overall hierarchy doesn't become to deep.
In the first step we can just link to a PPC site which we think
fits best. The way of naming wikis and organize them, will be
the same for all processor types.
Right now, we can link to some of the PPC pages just for information.

> **calebio said:**
> I like this effort and would be happy to help out. My **first comment** is in regards to getting to this new set of pages. When I look for documentation on Ubuntu, I often start at _[www.ubuntu.com]("http://www.ubuntu.com")_, click Community > Help and Information > Documentation and end up _[here]("https://help.ubuntu.com/community/")_.

Then, for my MacBook Pro (or other previous laptops), choosing _[Installation]("https://help.ubuntu.com/community/Installation")_ > Laptops I get to the _[Laptop Testing Team Apple Macintosh]("https://wiki.ubuntu.com/LaptopTestingTeam/Apple_Macintosh")_ page, at which point i get lost and confused, as that is all very hardware-specific and old.

Can that page get linked to the new _[Mactel Support page]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")_, or subsumed by it?
I think I will try to contact the Laptop Testing team to see what they say. As far as I know, that is really a separated thing from what we are doing (the community vs cannonical).

> **beauman said:**
> **Second note**, can the _[MacBook Aluminum]("https://help.ubuntu.com/community/MacBook%20Aluminum")_ page be linked from the _[Mactel Support Page]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")_ as a new item for 'MacBookPro5,1'? I see that one is help.ubuntu and the other wiki.ubuntu. Sounds like the latter is out of place:I will check this. You too can edit the wiki pages though... Just need a launchpad account. ;)

---

### Post by kosumi68 on 2008-11-05
Regarding target users, and I asked the question before whether Mac or Windows users are most likely to try Ubuntu, my guess is that the Windows users will outnumber the Mac users. By far. From this, I would draw the conclusion that the people reaching for the ubuntu help pages are people that have some knowledge, like the hardware, and want to try something new.

---

### Post by beauman on 2008-11-06
Ok. 

Now we all agree, that our page is focused on Intel based Macs
and that we mention other platforms like PPC or virtual machines
somewhere out of focus.

It's cool, that [MactelSupportTeam/CommunityHelpPages]("MactelSupportTeam/CommunityHelpPages")
is not listed under "multimedia apps"
anymore. That's one point of confusion less. :)

Maybe I misunderstand the meaning of

> **cyberdork33 said:**
> 
Quote:
Originally Posted by [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
Welcome to the Ubuntu Community Team Wiki!
This is THE definitive place for members of the Ubuntu community to discuss ideas and store team-related information.


Does it mean that this site contains information for a everybody,
but can only be edited be groups like us? 
(then it would be placed ok and I'm sorry)

Or does it mean it's just for internal group work and should not
be seen by the user who seeks help (like I thought until today)

A last approach of me, getting the title a bit more transparent 
for a newbee to mactel:

What do you think of:

"Ubuntu on Intel based Macs - MactelSupportTeam/CommunityHelpPages"?

( I promise not mentoin this subject again no matter what your answers are :) )

Thanks for beeing so patient with me.

So long,
beauman

---

### Post by cyberdork33 on 2008-11-06
> **beauman said:**
> It's cool, that [MactelSupportTeam/CommunityHelpPages]("http://MactelSupportTeam/CommunityHelpPages")
is not listed under "multimedia apps"
anymore. That's one point of confusion less. :)
?

> **beauman said:**
> Does it mean that this site contains information for a everybody,
but can only be edited be groups like us? 
(then it would be placed ok and I'm sorry)

Or does it mean it's just for internal group work and should not
be seen by the user who seeks help (like I thought until today)
No, it just means that it is a wiki where team information and coordination can be done. It is still just a ,wiki, it can be seen by anyone, and edited by anyone with a launchpad account just like the support wiki.

> **beauman said:**
> A last approach of me, getting the title a bit more transparent 
for a newbee to mactel:

What do you think of:

"Ubuntu on Intel based Macs - MactelSupportTeam/CommunityHelpPages"?

( I promise not mentoin this subject again no matter what your answers are :) )

I do think we need to Have something like this in the page, but making that the actual name of the page makes for one long URL. I'd also hesitate to change the team name (which is really the more logical solution for the problem), but the mactel-support team is already recognized by many and all our ppa and launchpad groups are setup with the same name (as well as the project name for tracking bugs).

Ok maybe we can make a page that is just titled "Ubuntu on Apple Hardware" and have the links to the Mactel team pages and to the PowerPC pages from there. Then we can maintain the mactel pages as specific to Intel and the PowerPC folks can still maintain their FAQ and such however they like.

---

### Post by freakalad on 2008-11-06
OK. 
When do we start & how can I help?

---

### Post by beauman on 2008-11-07
> **cyberdork33 said:**
> ?
Quote:
Originally Posted by beauman View Post
It's cool, that MactelSupportTeam/CommunityHelpPages
is not listed under "multimedia apps"
anymore. That's one point of confusion less.
?


In the left upper corner it used to be listed
under "multimedia apps". That changed now. 
Don't know why. Never mind. Not important.


> **cyberdork33 said:**
> 
No, it just means that it is a wiki where team information and coordination can be done. It is still just a ,wiki, it can be seen by anyone, and edited by anyone with a launchpad account just like the support wiki.
 Ok, I finally understood it. Sorry for beeing lame :)

> **cyberdork33 said:**
> 
I do think we need to Have something like this in the page, but making that the actual name of the page makes for one long URL. I'd also hesitate to change the team name (which is really the more logical solution for the problem), but the mactel-support team is already recognized by many and all our ppa and launchpad groups are setup with the same name (as well as the project name for tracking bugs).


Ok, accepted. I spoke just out of my own experience. I
installed Ubuntu on my Mac maybe three weeks ago and I
googled for "MacBook Ubuntu" really really a lot of times. 
I remember, that I somewhere saw the word "Mactel". But
since I didn't know the meaning of it, I never followed
such a link. 

We will find ways to guide everbody to our
site, no matter if he knows what "Mactel" is or not.
Everthing is going to be great :)

@druggo and calebio: 

Welcome to the mactel-support social group! :)

@freakalad: We are still in a brainstorming phase, but things are
getting more concrete at the moment.
If you like, you can join our group: [http://ubuntuforums.org/group.php?groupid=352]("http://ubuntuforums.org/group.php?groupid=352")

It's cool that the group is getting better.
This is so far what we have as different hadware:
20" iMac C2D (iMac5,1) - cyberdork33
MacBookAir1,1          - kosumi68
MacBook Pro            - calebio
MacBook 4,1            - beauman

drugo, what is your hw?
Anybody with other macel hw?

I also have a quite freaky idea about testing
ubuntu on Macs, whitout installing it there.
It's about cloning it to a USB stick and booting
it with isolinux. More to that later.

Question: Do you think we should have a sandbox or some kind
of an internal shadow page for the community help pages?
So we can discuss changes not in public.

We should also have a TODO-list somewhere.

I start it here and maybe somebody can please copy it to
[https://wiki.ubuntu.com/MactelSupportTeam]("https://wiki.ubuntu.com/MactelSupportTeam")

Please extend and life it!

* Make a comprehensive list of *all* Mactel product and their
  respective hardware ID's and even more important, their 
  production time
* Find people who have such a hardware and who like to act as
  wiki maintainers for such a page.
* Write down guidelines for our group, how we think the 
  community help page should look like and how we
  recommend to write wikis for Macs. What we expect
  from wiki maintainers associated to us (like testing
  upcomming beta versions and that stuff)
* Write a template for a Mac wiki
* Clean up dead links like 
  [https://help.ubuntu.com/community/mactel]("https://help.ubuntu.com/community/mactel")
* Rewrite [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages"), so it has 
    - a nice introduction (that explains words like mactel or PPA)
    - an abstract of the installation
    - common things, things about the Mac side and booting
    - the table that links all available hw to all ubuntu versions we recommend
    - other stuff like ubuntu on PPC Macs or on virtual machines (VM)
* Collect picture material of all Macs



Greetz from vienna, beauman

---

### Post by calebio on 2008-11-07
> **beauman said:**
> @druggo and calebio: 

Welcome to the mactel-support social group! :)

It's cool that the group is getting better.
This is so far what we have as different hadware:
20" iMac C2D (iMac5,1) - cyberdork33
MacBookAir1,1          - kosumi68
MacBook Pro            - calebio
MacBook 4,1            - beauman

Anybody with other macel hw?


I also have a 24" white iMac (iMac6,1) on which I now have Intrepid running quite well. It has the bluetooth wireless mouse and keyboard, which present their own _[specific problems]("http://ubuntuforums.org/showthread.php?t=963641")_.

I look forward to _[solving more problems]("http://ubuntuforums.org/showthread.php?t=971236")_ and getting the solutions out there.

---

### Post by kosumi68 on 2008-11-07
Calebio,

the iMac6 is not explicitly supported by applesmc, so it would be great if you would like to run the applesmc-test.sh script and report the output of scan-smc.sh in this thread: [http://ubuntuforums.org/showthread.php?t=924096](http://ubuntuforums.org/showthread.php?t=924096)

Thanks!

---

### Post by beauman on 2008-11-07
> **freakalad said:**
> OK. 
When do we start & how can I help?

See [https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam)

---

### Post by cyberdork33 on 2008-11-07
> **beauman said:**
> If you like, you can join our group: [http://ubuntuforums.org/group.php?groupid=352](http://ubuntuforums.org/group.php?groupid=352)
Note that is only the "social group" for the forum. There are also the launchpad groups. (You need a launchpad account to do any wiki editing, plus it will get you a cool icon):
Mainly Programmers:
[https://launchpad.net/~mactel-support](https://launchpad.net/~mactel-support)

Anybody:
[https://launchpad.net/~mactel-support-community](https://launchpad.net/~mactel-support-community)

Note that there is a mailing list for launchpad teams so we can communicate that way as well.

> **beauman said:**
> I also have a quite freaky idea about testing
ubuntu on Macs, whitout installing it there.
It's about cloning it to a USB stick and booting
it with isolinux. More to that later.
This is a big issue that would be really good to have fixed. There is a HUGE thread on booting from USB devices linked in the FAQ with lots of info on this (nothing that really works).

> **beauman said:**
> Question: Do you think we should have a sandbox or some kind
of an internal shadow page for the community help pages?
So we can discuss changes not in public.
This is a good idea.

> **beauman said:**
> We should also have a TODO-list somewhere.

I start it here and maybe somebody can please copy it to
[https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam)


Looks like it made it to the page and it looks great.

> **calebio said:**
> I also have a 24" white iMac (iMac6,1) on which I now have Intrepid running quite well. It has the bluetooth wireless mouse and keyboard, which present their own _[specific problems]("http://ubuntuforums.org/showthread.php?t=963641")_.

I look forward to _[solving more problems]("http://ubuntuforums.org/showthread.php?t=971236")_ and getting the solutions out there.
Please add any specific information to the iMac page that might be helpful:
[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

I am thinking we may need to at least split the iMacs into White (5,1 and 6,1) and Aluminum (7,1+)

---

### Post by beauman on 2008-11-08
> **cyberdork33 said:**
> 
This is a big issue that would be really good to have fixed. There is a HUGE thread on booting from USB devices linked in the FAQ with lots of info on this (nothing that really works).


Hmm, my version is quick & dirty. I have just copied 
a working ubuntu to a stick and installed grub in the MBR
To boot it for BIOSes without USB support, I normally use a
supergrub CD that I fitted to my needs. But on the
Mac it says "loading stage one" and that all...

I thought, if Isolinux works for the installation CD,
it should also boot my stick. The advantage of isolinux
is, that it works without bios support for USB. The
disadvantage is, that it doesn't have such a nice device-
selection menu like supergrub. So you need to have several
boot entries depending on the position of the stick (sdb, sdc,...)

I tried to explain it here a bit, see my last post:
[http://ubuntuforums.org/showthread.php?t=937259]("http://ubuntuforums.org/showthread.php?t=937259")

My count for booting it on different machines is 15
at the moment, it's really a nice game to try it
everywhere :)

I started writing a "working matrix" for us today. The
tables are a bit tricky I have to admit ...;)

Friendly regards!!
beauman

---

### Post by cyberdork33 on 2008-11-08
> **beauman said:**
> I started writing a "working matrix" for us today. The
tables are a bit tricky I have to admit ...;)
Yes, and it is looking good already. I really dislike the tables too. This wiki software is pretty limited.

---

### Post by calebio on 2008-11-08
> **beauman said:**
> We should also have a TODO-list somewhere.

I start it here and maybe somebody can please copy it to
[https://wiki.ubuntu.com/MactelSupportTeam]("https://wiki.ubuntu.com/MactelSupportTeam")

I like this list and have started working on it. **Assigned to** sounds like too much obligation, so I changed it to **contributors**. :P  More to the point, though, since this is all volunteer, I don't see it as assignments (single), but rather group collaboration (multiple).

I have drafted some icons for the features [works/needs changes/does not work] idea. I welcome feedback.

The 'abstract installation' is very important. I think it involves reading all the existing instructions on all the version-specific pages and distilling the parts that are common. I've got them all open here on my computer and will wile away this wintery night with them. Check back _[here]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")_ and *please* provide feedback.

EDIT: Generic installation procedure drafted. I think the next step is to revise the hardware-specific pages to link to the primary page and replace the step-by-step instructions on them with, say, the following:
> Basic installation instructions for Ubuntu on a Mactel are given _[here]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")_. This page gives details of installation and configuration that are specific to this hardware.

---

### Post by cyberdork33 on 2008-11-08
> **calebio said:**
> I like this list and have started working on it. **Assigned to** sounds like too much obligation, so I changed it to **contributors**. :P  More to the point, though, since this is all volunteer, I don't see it as assignments (single), but rather group collaboration (multiple).
excellent

> **calebio said:**
> I have drafted some icons for the features [works/needs changes/does not work] idea. I welcome feedback.Those are very good, and the idea is very obvious. I can send the svg of that logo if you PM me an email address. It might be easier to work with.

> **calebio said:**
> EDIT: Generic installation procedure drafted. I think the next step is to revise the hardware-specific pages to link to the primary page and replace the step-by-step instructions on them with, say, the following:
I think that the "Generic Installation Procedure" should go in it's own page in the help wiki somewhere. We should also consider single, dual, and triple booting. The MacBook Pro page has a good idea of how to handle that, but it is a bit of a mess right now.

I also just posted my install how to for my iMac on my blog, it might be helpful for filling in some info for a generic install (as it is about as generic as they get).
[http://www.rickycampbell.com/imac51-and-intrepid/](http://www.rickycampbell.com/imac51-and-intrepid/)

---

### Post by beauman on 2008-11-09
> **calebio said:**
> I like this list and have started working on it. **Assigned to** sounds like too much obligation, so I changed it to **contributors**. :P  More to the point, though, since this is all volunteer, I don't see it as assignments (single), but rather group collaboration (multiple).


Great! That's better. It's good that we correct each other!  

> **calebio said:**
> 
I have drafted some icons for the features [works/needs changes/does not work] idea. I welcome feedback.


I like them! Very good!

If we put a table at the beginning of a hardware wiki,
that lists all features and their support, so a user can see at one 
glance, if he likes to install ubuntu or not, can you maybe check, 
how the icons would look like in such a table?

> **calebio said:**
> 
The 'abstract installation' is very important. I think it involves reading all the existing instructions on all the version-specific pages and distilling the parts that are common. 


Yes. It should give the user an overview, of what he will have to
do, to make Ubuntu work on his hardware, to encourage him to
install it. 

Hey cyberdork33, I had a look at your pages. You have been very busy,
respect! :)

Greetz beauman

---

### Post by beauman on 2008-11-09
I'am confused about the release dates of the MacBooks. The
actual one is 5,1, but [http://en.wikipedia.org/wiki/Macbook]("http://en.wikipedia.org/wiki/Macbook") shows six hardware revision...
See the working matrix, how I think the dates are. Please edit it, if it's incorrect!
thanks, beauman

---

### Post by cyberdork33 on 2008-11-09
> **beauman said:**
> I'am confused about the release dates of the MacBooks. The
actual one is 5,1, but [http://en.wikipedia.org/wiki/Macbook](http://en.wikipedia.org/wiki/Macbook) shows six hardware revision...
See the working matrix, how I think the dates are. Please edit it, if it's incorrect!
thanks, beauman
I would guess that two models in that table have the same version number since many are essentially the same hardware...

I was wondering where you were getting the data for that. You might check here as well:
[http://www.apple-history.com/](http://www.apple-history.com/)
[http://mactracker.dreamhosters.com/](http://mactracker.dreamhosters.com/)

There are also Apple KB articles for each such as this one:
[http://support.apple.com/kb/SP23](http://support.apple.com/kb/SP23)

---

### Post by beauman on 2008-11-09
Great! MacTracker is what I was looking for! Perfect!

---

### Post by kosumi68 on 2008-11-09
Seems you've been busy, you too :-)

Great work!

---

### Post by cyberdork33 on 2008-11-09
> **beauman said:**
> Great! MacTracker is what I was looking for! Perfect!
Stream303 lead me here too:
[http://www.everymac.com/](http://www.everymac.com/)

---

### Post by beauman on 2008-11-10
Welcome shivathreya to the Mactel Support Team! :)

What kind of Mac hardware do you have?

---

### Post by calebio on 2008-11-12
> **calebio said:**
> ... I think the next step is to revise the hardware-specific pages to link to the primary page and replace the step-by-step instructions on them with, say, the following:

```
Basic installation instructions for Ubuntu on a Mactel are given _[here]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Generic%20Installation%20Procedure")_. This page gives details of installation and configuration that are specific to this hardware. 
```

Is there any reason not to do this? I think we could shorten several pages and consolidate versions into one reference point by doing so. But I don't want to upset anyone by removing existing content.

---

### Post by beauman on 2008-11-13
> **calebio said:**
> Is there any reason not to do this? I think we could shorten several pages and consolidate versions into one reference point by doing so. But I don't want to upset anyone by removing existing content.

I think so too. Before we replace the basic install instructions 
in each Mac wiki, we should have the "Mac-side and Booting" page
ready.

Should we put it in a new page or should we leave it on the start page?
What should it contain? How should it be titled
- refit (with hints on enable.sh, conf.sh, sync GPT with MBR, english keyboard layout)
- partitioning
  - bootcamp
  - diskutil
  - dual boot
  - triple boot (linux needs swap file instead of swap partition...)
- if we recommend to delete OS X
- where to get Ubuntu, how to burn and install it (hint on installing
  grub in the MBR of the partition rather than in the disk MBR) ...


What else?

I thought about putting links to 
[https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam) at the end of each wiki.
Mainly for the writers, so everbody who works on the wiki
gets to know our ideas. So we can prepare everybody, that
pages get renamed or moved... You are right,
we don't want to upset anybody.

So long, beauman

---

### Post by cyberdork33 on 2008-11-13
> **beauman said:**
> I think so too. Before we replace the basic install instructions 
in each Mac wiki, we should have the "Mac-side and Booting" page
ready.+1


> **beauman said:**
> Should we put it in a new page or should we leave it on the start page?
It should be a new page in the community help wiki, not the team wiki.
> **beauman said:**
> What should it contain? How should it be titled
- refit (with hints on enable.sh, conf.sh, sync GPT with MBR, english keyboard layout)
- partitioning
  - bootcamp
  - diskutil
  - dual boot
  - triple boot (linux needs swap file instead of swap partition...)
- if we recommend to delete OS X
- where to get Ubuntu, how to burn and install it (hint on installing
  grub in the MBR of the partition rather than in the disk MBR) ...

try to link official documentation where you can. Less to maintain. i.e. rEFIt install instructions and information is already on the rEFIt website.

For partitioning, there is DiskUtility and diskutil. They are different. Also, for a triple-boot, you do not HAVE to have a swapfile. A swap partition will wok just fine.

I would never recommend that someone removes OSX. People can use their computer however they like. In fact, I would be more inclined to recommend they NOT delete osx because of firmware updates.

> **beauman said:**
> I thought about putting links to 
[https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam) at the end of each wiki.
Mainly for the writers, so everbody who works on the wiki
gets to know our ideas. So we can prepare everybody, that
pages get renamed or moved... You are right,
we don't want to upset anybody.
That is a good idea. We can have a little section at the end of the wiki pages that says something along the lines of "This page is maintained by members of the MactelSupportTeam. If you are interested in helping, please visit our team page for information."
The contributor/maintainer should also be sure to subscribe to the pages to watch for changes that others might be making.

---

### Post by beauman on 2008-11-13
> **cyberdork33 said:**
> 

It should be a new page in the community help wiki, not the team wiki.

ok

> **cyberdork33 said:**
> 
try to link official documentation where you can. Less to maintain. i.e. rEFIt install instructions and information is already on the rEFIt website.

I just like to give some hints here, about the swapped "y" and "z"

> **cyberdork33 said:**
> 
For partitioning, there is DiskUtility and diskutil. They are different. 


Ok. I don't know DiskUtility. Since most of the wikis here at Mactel 
explain to use boot camp, I like to suggest also 
diskutil list
diskutil resizeVolume "/Volumes/Macintosh HD" limits
sudo diskutil resizeVolume disk0s2 75G

cd33, can you recommand DiskUtility as a third way to partition?
(I tried first with the GUI tools from OSX, but didn't make it.
Maybe because I never really updated the software) Can you post a 
screenshot?

> **cyberdork33 said:**
> 
Also, for a triple-boot, you do not HAVE to have a swapfile. A swap partition will work just fine.

No experience with this. We have to relay on what exists.

> **cyberdork33 said:**
> 
I would never recommend that someone removes OSX. People can use their computer however they like. In fact, I would be more inclined to recommend they NOT delete osx because of firmware updates.

Yes, that's what I ment. Somebody asked for it lately.

> **cyberdork33 said:**
> 
That is a good idea. We can have a little section at the end of the wiki pages that says something along the lines of "This page is maintained by members of the MactelSupportTeam. If you are interested in helping, please visit our team page for information."
The contributor/maintainer should also be sure to subscribe to the pages to watch for changes that others might be making.
:):):)

Cd33, what about [http://www.rickycampbell.com/imac51-and-intrepid/?](http://www.rickycampbell.com/imac51-and-intrepid/?)
Do you like it to be merged into our section?

calebio, I have marked it started...

Maybe we first write the new title & new destination in the existing
doc at [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages"), so we can create it in some days,
when everybody has had the opportunity to change it.

I'm also going to make some pictures of rEFIt and step7 install menu
ubuntu "advanced".

So long for today,
greetz beauman

---

### Post by cyberdork33 on 2008-11-13
> **beauman said:**
> I just like to give some hints here, about the swapped "y" and "z"
Yes, having generalized info is good, but don't go into the steps of installing since it is already there. The swapped keys issue is a good one to address. There is actually a lot of problems with international Apple Keyboards not working correctly. (swapped keys mostly, no AltGr key)

> **beauman said:**
> Ok. I don't know DiskUtility. Since most of the wikis here at Mactel 
explain to use boot camp, I like to suggest also 
diskutil list
diskutil resizeVolume "/Volumes/Macintosh HD" limits
sudo diskutil resizeVolume disk0s2 75G that is good, just need to be more careful with that method since typos can lead to disaster a little easier. I usually say this is an "advanced method" (see Intel_iMac page)

> **beauman said:**
> cd33, can you recommand DiskUtility as a third way to partition?
(I tried first with the GUI tools from OSX, but didn't make it.
Maybe because I never really updated the software) Can you post a 
screenshot?In Leopard, yes. You almost have to use the commandline method with Tiger. I will try to get some pics when I have a chance (Other things going on you know).

> **beauman said:**
> Cd33, what about [http://www.rickycampbell.com/imac51-and-intrepid/?](http://www.rickycampbell.com/imac51-and-intrepid/?)
Do you like it to be merged into our section?sure. Share and share alike. I have no restrictions on what I write in the blog.

---

### Post by beauman on 2008-11-14
I put a "overview" box and links to our team in [https://wiki.ubuntu.com/MacBook/SantaRosa]("https://wiki.ubuntu.com/MacBook/SantaRosa")

@calebio: I used the icons from [https://help.ubuntu.com/community/IconsPage]("https://help.ubuntu.com/community/IconsPage") and uploaded
a selfmade icon.

Any feedback  appreciated.

-beauman-

EDIT: cyberdork33,  I altered the text you suggested a little. 


Can somebody merge the missing sections into the wiki?
Apple IR, Disable Touchpad While Typing, ...

Maybe we can get this page as good as we can, to than use it as a template? It's almost there, I would say...

---

### Post by kosumi68 on 2008-11-14
> **beauman said:**
> I put a "overview" box and links to our team in [https://wiki.ubuntu.com/MacBook/SantaRosa]("https://wiki.ubuntu.com/MacBook/SantaRosa")


Cool stuff! It gives a great overview of what is working, what requires tweaking, and what does not work. I can haz copy pawst? :-)

---

### Post by beauman on 2008-11-15
[Template]("https://wiki.ubuntu.com/MactelSupportTeam/DocTemplate") started

---

### Post by beauman on 2008-11-16
Hi everybody! It's Sunday and maybe time for a little 
group work...

I've updated our internal [working page]("https://wiki.ubuntu.com/MactelSupportTeam") a bit and would
like to discuss the status of our project.

I have created the doc template. Maybe in the wrong place,
references to the community help wikis don't work.
Is there something special about creating a doc template,
and how can we make it available to users? (Maybe somebody
can just create & copy it?)

How do you like [MacBook/SantaRosa]("https://wiki.ubuntu.com/MacBook/SantaRosa")? Is it too much with the picture and all the
small icons? 

Would you like to edit the wikis for your MAC hardware, so they
look the same? And upload pictures?

But we should probably first finish some guidelines for our wikis.

@ calebio: You have started an abstract of the installation, and
we have talked about a common page about OS X, installing, booting
and common recommendations, would you like to continue it?

I would then like to start with the guidelines.

Also, we have to agree on a naming/structuring theme. 
 - Should the release date go into the title?
 - Should we have a single wiki for several modell revisions?

@freakalad, druggo, shivathreya: Please don't be so shy! :)

Hardware support in our team: We need quite urgently somebody
with a MacBook/Pro/mini of the first or second generation. That would
cover six different MACs...

And maybe somebody knows a Mac Pro owner? I have mailed with
people from the wiki histories, without any success. So
I added a info box about our team at the end of Mactel
wikis, which we are probably going to link.

So long for today,
have a nice Sunday afternoon,
-beauman-

---

### Post by beauman on 2008-11-16
> 
> Hey Jens-Christian,
> 
> Thanks. I was actually trying to figure out what the best way to 
> reorganize those macbook pages on help.ubuntu.com would be as they 
> have gotten quite cluttered. The page you linked to is a lot nicer! 
> 
> I looked on the mactel-support wiki page trying to see if the team 
> used a mailing list to coordinate changes, but didn't see one. Do you 
> basically just use the TODO lists on the wiki page? What's the best 
> way for me to help out and make sure I'm not stepping on anyone's 
> toes?


hi!  

The wiki you used is aimed at MacBooks v1.1 and v2.1. The wiki for 8.04 and MB v3,1 and 4,1 is this one:
[MacBook_Santa_Rosa]("https://help.ubuntu.com/community/MacBook_Santa_Rosa")

Funny, because I made the same mistake and that's how I came into this project.  :)

We don't have a mailing list yet. At the moment we discuss everything here.

I saw you already joined the group, great!!!



If you like to start, you can take care of a new page for thinks,
that apply to all Mactel installations, like resizing the HFS+ partition,
installing and enabling the bootloader and installing linux.
we talked about it a bit here:
> **beauman said:**
> I... Before we replace the basic install instructions in each Mac wiki, we should have the "Mac-side and Booting" page ready.

Should we put it in a new page or should we leave it on the start page?
What should it contain? How should it be titled
- refit (with hints on enable.sh, conf.sh, sync GPT with MBR, english keyboard layout)
- partitioning
  - bootcamp
  - diskutil
  - dual boot
  - triple boot (linux needs swap file instead of swap partition...)
- if we recommend to delete OS X
- where to get Ubuntu, how to burn and install it (hint on installing
  grub in the MBR of the partition rather than in the disk MBR) ...
 and the following posts.

I proposed a name for this page here: [Ubuntu on Mactel, Common]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Generic%20Installation%20Procedure"), but 
maybe you can think of a more appropriate name. Maybe we should call it
just "Generic Installation Procedure".

You can actually look at all the Mactel wikis and copy a lot from there.
I would like to have maybe a screenshot from the installation step 7
with the advanced option to place grub in the MBR of the partition rather
than in the MBR of the disk. ( I think this option would better
fit into step 5 where you do all the partitioning stuff) and 
a pic of refit. (I am going to upload one)

I proposed today also to caledio to work on this page.

I am going to start with writing guidelines.

Ok, but take your time and welcome!

beauman

---

### Post by cyberdork33 on 2008-11-16
Excellent Progress. I am a little preoccupied right now as you know so I will not be able to contribute much very soon, but so far this is looking great and I will definitely use your template for the Intel iMac page when I can get to it.

---

### Post by shufei4520564 on 2008-11-17
is [runescape power leveling](http://www.runescape-shop.com/runescape-power-leveling/runescape-power-leveling.php) safe??every one know.

---

### Post by beauman on 2008-11-17
Hi! I started with the guidelines, please have a look at it. Please
correct typos and strange words I used. Thanks a lot!

The template is also moved to help.ubuntu.com.

So long beauman

---

### Post by kosumi68 on 2008-11-17
I had a look at the guidelines. I cannot really stand by recommendations like 'think mac, not linux'. This is, after all, a linux community. Tech language belongs here. Regarding the large purple notices, it is a bit too much, isnt it. The review idea behind is interesting, but it becomes somewhat arbitary. Linking to alternatives or leaving precise notes where appropriate might have better effect.

Thanks for the effort, it is much appreciated!

---

### Post by beauman on 2008-11-18
> **kosumi68 said:**
> I had a look at the guidelines. I cannot really stand by recommendations like 'think mac, not linux'. This is, after all, a linux community. Tech language belongs here. Regarding the large purple notices, it is a bit too much, isnt it. The review idea behind is interesting, but it becomes somewhat arbitary. Linking to alternatives or leaving precise notes where appropriate might have better effect.

Thanks for the effort, it is much appreciated!

Hi kosumi68! 

It is a first draft. I have guessed, that the guidelines might
be criticized. They reflect my wish of getting Ubuntu ready
for everybody. It's not the first time, that Linux people disagreed 
with me in this point.

The guidelines are an  essential point of our documentation project.
So, please rewrite them, that you can stand behind them!! 
Delete everything that you think is crap and rewrite it, so everybody
 from MactelSupport can stand behind it! :) 
-beauman-

[EDIT] I also saw, that you changed the "pointer" page "MacBook Air" into "MacBookAir".
Well, it was just my point, to name things with the offical markting name.
One idea is to help search machines find it, when you google for "ubuntu MacBook Air".
It also looks more official. 

When the wiki "MacBook Air 2,1 on Ubuntu 9.04 (Jaunty Jackalop) has
reached a "stable" state, the pointer will be redirected to this page.

---

### Post by kosumi68 on 2008-11-18
> **beauman said:**
> 
The guidelines are an  essential point of our documentation project.
So, please rewrite them, that you can stand behind them!! 
Delete everything that you think is crap and rewrite it, so everybody
 from MactelSupport can stand behind it! :) 


How true it is, that as soon as one actually does something, critique will follow :-) But the text does require some softening.

> 
[EDIT] I also saw, that you changed the "pointer" page "MacBook Air" into "MacBookAir".
Well, it was just my point, to name things with the offical markting name.
One idea is to help search machines find it, when you google for "ubuntu MacBook Air".
It also looks more official. 


I also had that idea, initially (you might have seen several redirected pages). However, I realized that

1. Using the DMI format (one word) makes things easy

2. White space in names are prone for spelling errors

3. The automatic URL detection gets it wrong sometimes when spaces are present.

So, I moved away from space in the name for good reasons.

---

### Post by kosumi68 on 2008-11-18
> **beauman said:**
> 
When the wiki "MacBook Air 2,1 on Ubuntu 9.04 (Jaunty Jackalop) has
reached a "stable" state, the pointer will be redirected to this page.

There is a preposition problem with "machine on ubuntuversion". Either "machine running ubuntuversion" or "machine and ubuntuversion" or "ubuntuversion on machine" would work. It is also reflected in the current MBA page.

---

### Post by beauman on 2008-11-18
Yes you are right. It must be

MacBook Air 2,1 and Ubuntu 9.04 (Jaunty Jackalop)


I have to change it in the template as well.

So, do you think we should use this name as recommendation?

For several models it than would be:

MacBook Air 3,1 & 2,1 and Ubuntu 9.04 (Jaunty Jackalop)

With the release date(s) in the title it would get too long...


> **kosumi68 said:**
> ... But the text does require some softening.



Please go for it! Kick out what you don't like or rewrite it.


> **kosumi68 said:**
> 
I also had that idea, initially (you might have seen several redirected pages). However, I realized that

1. Using the DMI format (one word) makes things easy

2. White space in names are prone for spelling errors

3. The automatic URL detection gets it wrong sometimes when spaces are present.

So, I moved away from space in the name for good reasons.



Okey dokey. Without whitespaces then. I'am going to change it tonight.

---

### Post by beauman on 2008-11-18
Do you mean all pages without whitespace?

( I was just talking about the pointer pages you edited yesterday)

Like 
MacBookAir2,1andUbuntu9.04(JauntyJackalop)

:confused:

---

### Post by cyberdork33 on 2008-11-18
> **beauman said:**
> Do you mean all pages without whitespace?

( I was just talking about the pointer pages you edited yesterday)

Like 
MacBookAir2,1andUbuntu9.04(JauntyJackalop)

:confused:
The actual page titles should contain no whitespace (and actually should avoid special characters too). You can refer to the Machines in the text of the documents however you like (Macbook Air), but when referring to the version string, it should be the version string as it is shown (MacbookAir1,1). 

I would avoid relying on the wiki software to create links for you by just typing the page name in the text of a page, and instead create a full URL ( [[ http:\\the.fullurl.com\pagename | Link Text ]] )

---

### Post by beauman on 2008-11-18
> **cyberdork33 said:**
> 

I would avoid relying on the wiki software to create links for you by just typing the page name in the text of a page, and instead create a full URL ( [[ http:\\the.fullurl.com\pagename | Link Text ]] )

Yes, ok. Even for [[ http:\\the.fullurl.com\pagename | the.fullurl.com\pagename ]], the text gets a bit shorter. I like that.

> **cyberdork33 said:**
> The actual page titles should contain no whitespace (and actually should avoid special characters too).  


Comma and dot seem to be special characters:
[urlencoding.htm]("http://www.blooberry.com/indexdot/html/topics/urlencoding.htm")

Should we use them anyway? Moinmoin would not create the link
correct, but using the syntax cb33 suggested, would solve this
problem.

What do you think about:
[LIST]
[*]omitting the space, if within an expression and the right word starts with **capital letter**  (MacBook Air -> MacBookAir)
[*]replacing the space with underscore, if within an expression and the right word starts with a **lowercase** (Mac mini -> Mac_mini)
[*] using minus to separate hw, revision, Ubuntu version?
[*] using comma and dot anyway
[/LIST]

 
Mac_mini-2,1-and-Ubuntu-9.04-(JauntyJackalop)

That looks not too bad...

Friendly regards!

-beauman-

P.S.: Welcome nTia89 to the group!

---

### Post by kosumi68 on 2008-11-18
> **beauman said:**
> 
MacBook Air 3,1 & 2,1 and Ubuntu 9.04 (Jaunty Jackalop)


I still do not think mixing several machines is a good idea - if there is nothing differing but a few names, it should only mean the page is almost empty on text, containing only links to common instructions.

> 
Please go for it! Kick out what you don't like or rewrite it.


If you add 'beauman thinks' before the hot statements, everything is fine. Inducing a necessity for others to revise by claiming to speak for them does not feel completely... right.

---

### Post by kosumi68 on 2008-11-18
> **beauman said:**
> 
[LIST]
[*]omitting the space, if within an expression and the right word starts with **capital letter**  (MacBook Air -> MacBookAir)
[*]replacing the space with underscore, if within an expression and the right word starts with a **lowercase** (Mac mini -> Mac_mini)
[*] using minus to separate hw, revision, Ubuntu version?
[*] using comma and dot anyway
[/LIST]

 
Mac_mini-2,1-and-Ubuntu-9.04-(JauntyJackalop)

That looks not too bad...


Excellent - this will work nicely. :-)

---

### Post by kosumi68 on 2008-11-18
> **beauman said:**
> 
Mac_mini-2,1-and-Ubuntu-9.04-(JauntyJackalop)


Sorry for being such a nit-pick, but it is actually 'Jackalope'. The word refers to a fictional animal, a cross between a jackrabbit and an antelope, goat, or deer (wikipedia). Hence Ubuntu 9.04 means 'quick-footed jackrabbit-antelope'.

---

### Post by beauman on 2008-11-18
> **kosumi68 said:**
> 
Sorry for being such a nit-pick, but it is actually 'Jackalope'. The word refers to a fictional animal, a cross between a jackrabbit and an antelope, goat, or deer (wikipedia). Hence Ubuntu 9.04 means 'quick-footed jackrabbit-antelope'.

:):):)

> **kosumi68 said:**
> I still do not think mixing several machines is a good idea - if there is nothing differing but a few names, it should only mean the page is almost empty on text, containing only links to common instructions.

Yes, we can agree on this. It's clearer to the user. That means
for example, we split [wiki.ubuntu.com/MacBook/SantaRosa]("https://wiki.ubuntu.com/MacBook/SantaRosa") into two wikis,
when we move it to help.ubuntu.com. I was thinking about it, but dropped
the thought.

> **kosumi68 said:**
> 
If you add 'beauman thinks' before the hot statements, everything is fine. Inducing a necessity for others to revise by claiming to speak for them does not feel completely... right.

Come on. You can edit it. It's a wiki! And it's not me speaking here,
it's our group. Do it! I tried to soften it a bit today anyway.
I can number the points, and you can say: beauman, you have to
edit point 1,2, and point 10, if you really really think you can't do it.

---

### Post by regebro on 2008-11-18
What to do when I don't agree with the statement? That Sound works out of the box, on a 4,1 with 8.10 for example. Although it kinda depends on the definition of "works". :D

Should I just edit it? Nobody will get upset? :)

---

### Post by beauman on 2008-11-18
> **regebro said:**
> What to do when I don't agree with the statement? That Sound works out of the box, on a 4,1 with 8.10 for example. Although it kinda depends on the definition of "works". :D

Should I just edit it? Nobody will get upset? :)

Hi regebro! What exactly do you want to edit? We are actually talking about the guidelines. If you are looking for a wiki about MB 4,1 and Ubuntu 8.10
it's [here]("https://wiki.ubuntu.com/MacBook/SantaRosa").

@kosumi: I'm going to delete everything crappy now.

---

### Post by cyberdork33 on 2008-11-18
> **beauman said:**
> Comma and dot seem to be special characters:
[urlencoding.htm]("http://www.blooberry.com/indexdot/html/topics/urlencoding.htm") That is correct, although I don't think there is a problem with a period for most users as it is used quite a bit in URLs.

> **beauman said:**
> Should we use them anyway? Moinmoin would not create the link
correct, but using the syntax cb33 suggested, would solve this
problem.

What do you think about:
[LIST]
[*]omitting the space, if within an expression and the right word starts with **capital letter**  (MacBook Air -> MacBookAir)
[*]replacing the space with underscore, if within an expression and the right word starts with a **lowercase** (Mac mini -> Mac_mini)
[*] using minus to separate hw, revision, Ubuntu version?
[*] using comma and dot anyway
[/LIST]

 
Mac_mini-2,1-and-Ubuntu-9.04-(JauntyJackalop)

I really think we should keep the URL length to a minimum, and it should agree as best as it can with the version string... (help.ubuntu.com/community/Mac_mini-2,1-and-Ubuntu-9.04-JauntyJackalop would be a very hard URL to remember, plus, after each release you have to find the new URL to get the latest instruction). Macbook4,1 should be at help.ubuntu.com/community/Macbook4,1 (or maybe Macbook4-1 if we want to avoid the comma). Each page can have a "subpage" for previous releases, i.e. help.ubuntu.com/community/Macbook4,1/Hardy for the "archived" Hardy installation instructions and the main page reflects instruction only for the latest release. When Jaunty is release, we would then take the current Intrepid content and move it to help.ubuntu.com/community/Macbook4,1/Intrepid or something of the sort and freshen the content of the main page with info for Jaunty.

> **regebro said:**
> What to do when I don't agree with the statement? That Sound works out of the box, on a 4,1 with 8.10 for example. Although it kinda depends on the definition of "works". :D

Should I just edit it? Nobody will get upset? :)
It sounds like you are splitting hairs ;)

If the sound comes out of the machine, then it "works" if it doesn't sound pretty or something, it would be good to state so (and the fix if it exists), but I would not put that it "does not work". Along these lines, I would also treat the Microphone and Headphones socket separate from "sound" since they normally require some tweaking anyway.

---

### Post by regebro on 2008-11-18
> **cyberdork33 said:**
> Along these lines, I would also treat the Microphone and Headphones socket separate from "sound" since they normally require some tweaking anyway.

I'd say that is "manual installation" in that case, because evidently the bass speaker doesn't work, and the sockets doesn't work wither, unless you do stuff, and we need instructions for that. I'll change it tomorrow, I think, I'll see if I can figure out how to actually solve the problem first.

---

### Post by cyberdork33 on 2008-11-18
> **regebro said:**
> I'd say that is "manual installation" in that case, because evidently the bass speaker doesn't work, and the sockets doesn't work wither, unless you do stuff, and we need instructions for that. I'll change it tomorrow, I think, I'll see if I can figure out how to actually solve the problem first.
I agree that it needs to work to work completely, and the instruction to fix should be put there. I guess you could change the status to "partially working" if that makes you feel better :)

---

### Post by beauman on 2008-11-18
I updated the [**guidelines**]("https://wiki.ubuntu.com/MactelSupportTeam/DocGuidlines"), any feedback welcome.


@ cb33: What you are saying is  a very good idea.

> **cyberdork33 said:**
> 
I really think we should keep the URL length to a minimum, and it should agree as best as it can with the version string... 
 [IMG]https://wiki.ubuntu.com/MacBook/SantaRosa?action=AttachFile&do=get&target=check.png[/IMG]

> **cyberdork33 said:**
> 
...plus, after each release you have to find the new URL to get the latest instruction). 
 

Well, we still have the matrix from the community help pages, but anyway...

> **cyberdork33 said:**
> 
Macbook4,1 should be at help.ubuntu.com/community/Macbook4,1 (or maybe Macbook4-1 if we want to avoid the comma). 
 We stick with the comma I would say.
> **cyberdork33 said:**
> 
Each page can have a "subpage" for previous releases, i.e. help.ubuntu.com/community/Macbook4,1/Hardy for the "archived" Hardy installation instructions and the main page reflects instruction only for the latest release. When Jaunty is release, we would then take the current Intrepid content and move it to help.ubuntu.com/community/Macbook4,1/Intrepid or something of the sort and freshen the content of the main page with info for Jaunty.

[IMG]https://wiki.ubuntu.com/MacBook/SantaRosa?action=AttachFile&do=get&target=check.png[/IMG]

Let's do it this way. It's very clear and a like it a lot.

---

### Post by cyberdork33 on 2008-11-18
> **beauman said:**
> Yes, we can agree on this. It's clearer to the user. That means
for example, we split [wiki.ubuntu.com/MacBook/SantaRosa]("https://wiki.ubuntu.com/MacBook/SantaRosa") into two wikis,
when we move it to help.ubuntu.com. I was thinking about it, but dropped
the thought.
I think that we should, as a guideline, use separate pages for each version, but there are circumstances where separate pages are not needed. We could of course create the newer page and just link to the previous version's page. for instance, in the Macbook SantaRosa page, I don't think there is one difference between Mabook3,1 and Macbook4,1 for configuration...

Also, I forgot to mention, i like the little note boxes, as long as they are not overused.

---

### Post by kosumi68 on 2008-11-18
[QUOTE=beauman;6205841]I updated the [**guidelines**]("https://wiki.ubuntu.com/MactelSupportTeam/DocGuidlines"), any feedback welcome.
[QUOTE]

thankyouthankyouthankyou! This version is *so* much better.

---

### Post by kosumi68 on 2008-11-18
> **cyberdork33 said:**
> 
Macbook4,1 should be at help.ubuntu.com/community/Macbook4,1 (or maybe Macbook4-1 if we want to avoid the comma). Each page can have a "subpage" for previous releases, i.e. help.ubuntu.com/community/Macbook4,1/Hardy for the "archived" Hardy installation instructions and the main page reflects instruction only for the latest release. When Jaunty is release, we would then take the current Intrepid content and move it to help.ubuntu.com/community/Macbook4,1/Intrepid or something of the sort and freshen the content of the main page with info for Jaunty.


Yes, this is still the best idea. Since we all agree on this one, I will put it into action as soon as I can for the MBA page.

---

### Post by kosumi68 on 2008-11-18
Regarding the commas... it really does make things ugly. We have had 4,1 and 4.1 and 4-1 as suggestions. How about 41?

---

### Post by Nikos.Alexandris on 2008-11-18
> **kosumi68 said:**
> Regarding the commas... it really does make things ugly. We have had 4,1 and 4.1 and 4-1 as suggestions. How about 41?

Hi!

Is there a 4,2 (or 4.2 or 42) version anyway? Or even 3,2 etc.

Why not use MacBook 3, MacBook 4, MacBook 5?

---

### Post by beauman on 2008-11-19
> **cyberdork33 said:**
> I agree that it needs to work to work completely, and the instruction to fix should be put there. I guess you could change the status to "partially working" if that makes you feel better :)

EDIT: Nice job with the update of the wiki!


> **cyberdork33 said:**
> I think that we should, as a guideline, use separate pages for each version, but there are circumstances where separate pages are not needed. We could of course create the newer page and just link to the previous version's page. for instance, in the Macbook SantaRosa page, I don't think there is one difference between Mabook3,1 and Macbook4,1 for configuration...


I like the idea of having a wiki for each hardware revision of a mac.
It's very clear to a user and to the wiki writers,
simple to understand. It's at the moment a bit
more work with creating the pages, but we can handle that.
For future versions it's easy. If there is a new revision or
new Ubuntu version comming out, create the new one by copying
the old and go through the content.

> **kosumi68 said:**
> Yes, this is still the best idea. Since we all agree on this one, I will put it into action as soon as I can for the MBA page.

kosumi, please don't start with moving any pages yet. 

We first have to create the fundament for the new structure.
The community help pages has to be rewritten, we need a nice
intro and a page for generic Mactel installation instructions.
We have to get the guidelines ready, we need a list for all
Mactel pages which we like to keep, move or which we like to be deleted.
We have to sketch the new structure in a nice svg containing 
an area for wiki.ubuntu.com and help.ubuntu.com.
We have to mark pages for deletion or movement and provide
at least a month or maybe two the link of the svg of the new structure
in the header of these file. Also we have to state a link
for people who like to object.

> **kosumi68 said:**
> Regarding the commas... it really does make things ugly. We have had 4,1 and 4.1 and 4-1 as suggestions. How about 41?

41 would also be ok for. 

> **Nikos.Alexandris said:**
> Hi!

Is there a 4,2 (or 4.2 or 42) version anyway? Or even 3,2 etc.

Why not use MacBook 3, MacBook 4, MacBook 5?

Yes there is, have a look at the [internal working matrix]("https://wiki.ubuntu.com/MactelSupportTeam#Hardware/Software/Contributors%20Working%20Matrix%20(Ubuntu%208.10%20%22Intrepid%20Ibex%22)").

---

### Post by beauman on 2008-11-19
> **regebro said:**
> What to do when I don't agree with the statement? That Sound works out of the box, on a 4,1 with 8.10 for example. Although it kinda depends on the definition of "works". :D

Should I just edit it? Nobody will get upset? :)

Hi! I have just tested the issue with the sound together with
my colleagues. We think you are right. Under OS X the sound is more
sonorous. 

Friendly regards,
beauman

---

### Post by cyberdork33 on 2008-11-19
hmm.. something like Macbook41 will probably be the cleanest, but could be confusing... There are some ,2 variations, but these are usually education versions and the like. They are pretty much the same hardware, but the second digit can increment (check out some of the version strings on the older PPC macs...)

I still vote for the hyphen. It is a standard URL character, and it allows division between the first and second digit.

---

### Post by kosumi68 on 2008-11-19
> **cyberdork33 said:**
> 
I still vote for the hyphen. It is a standard URL character, and it allows division between the first and second digit.


It will work for me.

---

### Post by beauman on 2008-11-20
For me too.

---

### Post by beauman on 2008-11-20
> **cyberdork33 said:**
> 


I really think we should keep the URL length to a minimum, and it should agree as best as it can with the version string... 
(help.ubuntu.com/community/Mac_mini-2,1-and-Ubuntu-9.04-JauntyJackalop would be a very hard URL to remember, plus, after 
each release you have to find the new URL to get the latest instruction). Macbook4,1 should be at help.ubuntu.com/community/Macbook4,1 
(or maybe Macbook4-1 if we want to avoid the comma). Each page can have a "subpage" for previous releases, i.e. 
help.ubuntu.com/community/Macbook4,1/Hardy for the "archived" Hardy installation instructions and the main page reflects instruction 
only for the latest release. When Jaunty is release, we would then take the current Intrepid content and move it to 
help.ubuntu.com/community/Macbook4,1/Intrepid or something of the sort and freshen the content of the main page with info for Jaunty.





I think we should put the wiki at once in an Ubuntu version subpage. So that people see from the title what Ubuntu version it is about.
We have to put it into the subpage some day anyway. If we move it later, we get conflicts with links from outside our doing, if somebody
revers to a certain Ubuntu version. Also, there will be a time, where the wiki is in an unstable phase (or maybe even empty), when created.
I suggest that the toplevel site of this hardware revision (help.ubuntu.com/community/Macbook4-1/) will be a pointer page,
which redirects to the stable wiki of the latest Ubuntu version. 

If, for example, Jaunty will be launched in April, we will create  help.ubuntu.com/community/Macbook4-1/Jaunty maybe in March (or even when we create the new site structure). It will  have reached a stable state maybe a month after the release and we (re-)redirect the pointer page. It will also be linked in the matrix on the Mactel community page from that moment on, where we decide to support the new Ubuntu version. (Which should be latest with the release)

---

### Post by cyberdork33 on 2008-11-20
> **beauman said:**
> I think we should put the wiki at once in an Ubuntu version subpage. So that people see from the title what Ubuntu version it is about.
We have to put it into the subpage some day anyway. If we move it later, we get conflicts with links from outside our doing, if somebody
revers to a certain Ubuntu version. Also, there will be a time, where the wiki is in an unstable phase (or maybe even empty), when created.
I suggest that the toplevel site of this hardware revision (help.ubuntu.com/community/Macbook4-1/) will be a pointer page,
which redirects to the stable wiki of the latest Ubuntu version. 

If, for example, Jaunty will be launched in April, we will create  help.ubuntu.com/community/Macbook4-1/Jaunty maybe in March (or even when we create the new site structure). It will  have reached a stable state maybe a month after the release and we (re-)redirect the pointer page. It will also be linked in the matrix on the Mactel community page from that moment on, where we decide to support the new Ubuntu version. (Which should be latest with the release)
OK. I was trying to avoid having to go through more links, but that will work.

P.S. There was a note at the top of the MacBook page that said users should go to the MacBook SantaRosa page for help with Intrepid, but I removed it as the hardware for these machines are different.

---

### Post by kosumi68 on 2008-11-20
Ok, I moved/redirected all prior MacBook Air links to this page:

[https://help.ubuntu.com/community/MacBookAir1-1/Intrepid](https://help.ubuntu.com/community/MacBookAir1-1/Intrepid)

The generic page is currently redirecting to the page above:

[https://help.ubuntu.com/community/MacBookAir1-1/](https://help.ubuntu.com/community/MacBookAir1-1/)

I am prepared to set this in stone now :-)

---

### Post by cyberdork33 on 2008-11-20
> **kosumi68 said:**
> I am prepared to set this in stone now :-)
Me too

---

### Post by jrib on 2008-11-20
> **beauman said:**
> > 
I proposed a name for this page here: [Ubuntu on Mactel, Common]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Generic%20Installation%20Procedure"), but 
maybe you can think of a more appropriate name. Maybe we should call it
just "Generic Installation Procedure".


How about MactelInstallation?  I'll probably have some time tomorrow to get started on it.

Also, [https://help.ubuntu.com/community/AppleiSight](https://help.ubuntu.com/community/AppleiSight) is on the MacBook page.  Afaict, those instructions are common to mactels whose webcam don't work ootb.  [https://wiki.ubuntu.com/MacBook/SantaRosa](https://wiki.ubuntu.com/MacBook/SantaRosa) should probably just link to the AppleiSight page to avoid duplication of effort.

The plan seems to be to create one main page directing users to the appropriate subpage by hardware model.  In addition, common procedures will have their own page (Installation, isight) which will be linked to from the specific hardware model pages.  Have I got that right?

I'm not clear on how we are going to deal with different ubuntu versions though.  For the macbook, I think it makes sense to just have the subpage concentrate on Intrepid because Gutsy was a real pain with the macbook.  At the same time, supported ubuntu releases should have some documentation.  How about the hardware model subpages contain documentation on the latest supported ubuntu version and earlier versions that are supported but without too much extra trouble (this is subjective).  If there is a supported version that is not as easy to work with, it can be split off as MacBook/Gutsy for example.  Any instructions for unsupported versions should just be deleted.  Feedback on this?  Sorry if I missed some of the earlier discussion on this as I read the thread piecemeal.

This brings up another question.  In the NameOfThePage, should we use the codename (like Gutsy) or the version number (like 7.10)?

---

### Post by cyberdork33 on 2008-11-20
> **_jason said:**
> How about MactelInstallation?  I'll probably have some time tomorrow to get started on it.
In light of other comments made earlier, maybe something like "IntelMacInstallation" or " AppleIntelInstallation".

> **_jason said:**
> Also, [https://help.ubuntu.com/community/AppleiSight](https://help.ubuntu.com/community/AppleiSight) is on the MacBook page.  Afaict, those instructions are common to mactels whose webcam don't work ootb.  [https://wiki.ubuntu.com/MacBook/SantaRosa](https://wiki.ubuntu.com/MacBook/SantaRosa) should probably just link to the AppleiSight page to avoid duplication of effort.
Yes that is the plan. Actually, that is the OLD SantaRosa address. The documentation for Macbook3,1 and 4,1 should be here:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)
Note the address is subject to change according to the discussion we have had here.

> **_jason said:**
> The plan seems to be to create one main page directing users to the appropriate subpage by hardware model.  In addition, common procedures will have their own page (Installation, isight) which will be linked to from the specific hardware model pages.  Have I got that right?Sounds right to me.

> **_jason said:**
> I'm not clear on how we are going to deal with different ubuntu versions though.  For the macbook, I think it makes sense to just have the subpage concentrate on Intrepid because Gutsy was a real pain with the macbook.  At the same time, supported ubuntu releases should have some documentation.  How about the hardware model subpages contain documentation on the latest supported ubuntu version and earlier versions that are supported but without too much extra trouble (this is subjective).  If there is a supported version that is not as easy to work with, it can be split off as MacBook/Gutsy for example.  Any instructions for unsupported versions should just be deleted.  Feedback on this?  Sorry if I missed some of the earlier discussion on this as I read the thread piecemeal.This is basically what I was suggesting earlier. The reason we would keep the Gutsy page for the Macbook is because the information is already there... no reason to delete it.

 > **_jason said:**
> This brings up another question.  In the NameOfThePage, should we use the codename (like Gutsy) or the version number (like 7.10)?
Good question. I thought about this a little bit earlier, but I didn't bring it up. I think we have enough numbers already to deal with, but then most new users use the version number rather than the code name. What do others think?

---

### Post by kosumi68 on 2008-11-20
Yes, enough numbers already. MaxBookX-Y/Gutsy, MacBookX-Y/Hardy, MacBookX-Y/Intrepid, MacBookX-Y/Jaunty, that seems to be what we are aiming for.

---

### Post by beauman on 2008-11-20
> **cyberdork33 said:**
> 

P.S. There was a note at the top of the MacBook page that said users should go to the MacBook SantaRosa page for help with Intrepid, but I removed it as the hardware for these machines are different.

Yes, thanks. My fault. It was ment for users with version v3.1 and v4.1.

About the title:

The doc template suggests to state everything important in the
first line:
"This page aims to describe the steps needed, to fully enable all features of the x-th Generation MacHardware (release date: late 200x) when using Ubuntu x.xx, codename." 

You could also argue that it's IntrepidIbex, not just Intrepid...

We want it short so we have to make a compromise.

I also added a new page today to welcome new members:
[wiki.ubuntu.com/MactelSupportTeam/Welcome]("https://wiki.ubuntu.com/MactelSupportTeam/Welcome")
Any feedback appreciated.

Do you think I should move the mb santa rosa page right now? I placed
a note there that it is going to be moved. But I didn't thought
it is going to be that fast... Will the redirect work at all
from wiki.ubuntu.com to help.ubuntu.com?

---

### Post by kosumi68 on 2008-11-20
> **beauman said:**
> 
I also added a new page today to welcome new members:
[wiki.ubuntu.com/MactelSupportTeam/Welcome]("https://wiki.ubuntu.com/MactelSupportTeam/Welcome")
Any feedback appreciated.


Nice :-)

> 
Do you think I should move the mb santa rosa page right now? I placed
a note there that it is going to be moved. But I didn't thought
it is going to be that fast... Will the redirect work at all
from wiki.ubuntu.com to help.ubuntu.com?


I believe creating the new pages in the right place, and starting to copy the relevant portions into the right place is more important than to move the page. This way, you are also more free to rearrange online. A change has to have some benefit :-)

---

### Post by regebro on 2008-11-21
> **cyberdork33 said:**
> Yes that is the plan. Actually, that is the OLD SantaRosa address. The documentation for Macbook3,1 and 4,1 should be here:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)
Actually, THAT is the old one (Gutsy) and MacBook/SantaRosa is Intrepid. :)

The MacBook/SantaRosa is pretty good now, IMO. Since 3,1 and 4,1 is the same, maybe we can rename it to MacBook3-1/Intrepid and make MacBook4-1/Intrepid redirect to the first one?


Also [https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook) redirect to [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) which is not optimal, as that page is about 7.10 and 8.04 and 1,1/2,1, and you have to click around to find the correct page. Maybe we can make a table of models and versions and link to the correct pages, if they exist?

---

### Post by kosumi68 on 2008-11-21
> **regebro said:**
> Since 3,1 and 4,1 is the same, maybe we can rename it to MacBook3-1/Intrepid and make MacBook4-1/Intrepid redirect to the first one?


1. The wiki does not gracefully handle multiple redirects. If MacBook4-1 needs to redirect to MacBook4-1/Intrepid, and then MacBook4-1/Intrepid redirects to MacBook3-1/Intrepid, you will wrongly end up at the redirect page MacBook4-1/Intrepid.

2. The machines MB3 and MB4 are similar, but they are not the same. I would copy the same page into both MacBook3-1/Intrepid and MacBook4-1/Intrepid to start with, then break out common things if necessary. With time, the 3-1 and 4-1 page will diverge into unique pages.

---

### Post by beauman on 2008-11-21
> **regebro said:**
> Actually, THAT is the old one (Gutsy) and MacBook/SantaRosa is Intrepid. :)

The MacBook/SantaRosa is pretty good now, IMO. Since 3,1 and 4,1 is the same, maybe we can rename it to MacBook3-1/Intrepid and make MacBook4-1/Intrepid redirect to the first one?


Also [https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook) redirect to [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) which is not optimal, as that page is about 7.10 and 8.04 and 1,1/2,1, and you have to click around to find the correct page. Maybe we can make a table of models and versions and link to the correct pages, if they exist?

Hi regebro! This is a bit funny now, because we just reached the first
page of this thread. Yes, we plan to make such a table. 
An inofficial version is already published at [Mactel support team]("https://wiki.ubuntu.com/MactelSupportTeam/#Hardware/Software/Contributors%20Working%20Matrix%20(Ubuntu%208.10%20%22Intrepid%20Ibex%22)").

The table is going to be installed at [MactelSupportTeam/CommunityHelpPages]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages"). At
the moment we are very busy to create a "infra structure" for
all wikis about Intel Macs. We are going to provide a template, 
guidelines, a complete new naming scheme and a start page. 

The new naming scheme will also speak for it self.

The page you worked on [(SantaRosa)]("https://wiki.ubuntu.com/MacBook/SantaRosa") is going to be moved to 
[help.ubuntu.com/community/MacBook4-1/Intrepid]("https://help.ubuntu.com/community/MacBook4-1/Intrepid")
and
[help.ubuntu.com/community/MacBook3-1/Intrepid]("https://help.ubuntu.com/community/MacBook3-1/Intrepid")

(without guarantee, we didn't really finish on the naming convention yet)

Since there are a lot of people involved in working on this page,
I am going to do the moving very carefully. I will move it, when
we from the support team have the infra structure ready.

We would of course be very happy, if you could join us!! 
[support team]("http://ubuntuforums.org/group.php?groupid=352")

I think the wiki about MB4,1/Intrepid is almost done. The basic install
instructions, the Apple remote and Firewire sections still have to be finished. 
jrib is going to start with  a separate page for the install  page. 

If it's done, we need people to go through the pages for Hardy, since it's
a LTS version.

Friendly regards,
beauman

---

### Post by regebro on 2008-11-21
> **kosumi68 said:**
> 1. The wiki does not gracefully handle multiple redirects.So redirect to the right page from the start then. ;)

> I would copy the same page into both MacBook3-1/Intrepid and MacBook4-1/Intrepid to start with, then break out common things if necessary.Common things as the moment is everything. I know the machines are not the same, but the instructions are. If we break out common things to yet another page, then we get double redirects for both. ;)

> **beauman said:**
> Hi regebro! This is a bit funny now, because we just reached the first
page of this thread. Yes, we plan to make such a table. 
An inofficial version is already published at [Mactel support team]("https://wiki.ubuntu.com/MactelSupportTeam/#Hardware/Software/Contributors%20Working%20Matrix%20(Ubuntu%208.10%20%22Intrepid%20Ibex%22)").
Yes, I saw that one, bit it's a bit unwieldy and contains lots of information. I was thinking of one with just a list of models for rows, and ubuntu versions as columns, where you could click to go to the correct page, and have that on some sort of main page, that you will find when you google on "Installing Ubuntu on Macintosh" or something. I doubt that the MactelSupportTeam pages will rank very high on that sort of search.

---

### Post by regebro on 2008-11-21
Doublepost.

---

### Post by beauman on 2008-11-21
> **regebro said:**
> 

Yes, I saw that one, bit it's a bit unwieldy and contains lots of information. I was thinking of one with just a list of models for rows, and ubuntu versions as columns, where you could click to go to the correct page, and have that on some sort of main page, that you will find when you google on "Installing Ubuntu on Macintosh" or something. I doubt that the MactelSupportTeam pages will rank very high on that sort of search.

This one is just for our internal team coordination. The one we create at the start page will be just what you want. Actually, with the new naming scheme, it could already be created. Go for it, if you like to. 

Google will also find it. People really appreciate  what we are doing here, and they are going to link the new pages. We are also going to ask to install links at important Ubuntu entry points. The top page will only be for Intel based Macs. We are also going to create a top level page for all Macintosh, which could have the name you suggested, but first of all we are going to get the docs for the Mactel world straight.

---

### Post by cyberdork33 on 2008-11-21
> **regebro said:**
> Actually, THAT is the old one (Gutsy) and MacBook/SantaRosa is Intrepid. :)

The MacBook/SantaRosa is pretty good now, IMO. Since 3,1 and 4,1 is the same, maybe we can rename it to MacBook3-1/Intrepid and make MacBook4-1/Intrepid redirect to the first one?
I think you are misunderstanding. I know that the one at wiki.ubuntu.com is "newer"... what I was trying to say was that it should NOT be at wiki.ubuntu.com, but rather under help.ubuntu.com/community


> **regebro said:**
> Also [https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook) redirect to [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) which is not optimal, as that page is about 7.10 and 8.04 and 1,1/2,1, and you have to click around to find the correct page. Maybe we can make a table of models and versions and link to the correct pages, if they exist?The first address is invalid for this type of info which is why the redirection is there now. There is no other way to handle the URL changes.

---

### Post by regebro on 2008-11-21
> **cyberdork33 said:**
> I think you are misunderstanding. I know that the one at wiki.ubuntu.com is "newer"... what I was trying to say was that it should NOT be at wiki.ubuntu.com, but rather under help.ubuntu.com/community
Aha, I see.

---

### Post by jrib on 2008-11-22
I've started to merge all of the installation documentation into [https://wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation](https://wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation).  I noticed that some pages do not recommend creating a swap partition.  Does anyone have any thoughts on what should be recommended?

Personally, I'm for a swap partition because I believe it's needed to be able to hibernate.  Does a swap partition cause problems with bootcamp however?

---

### Post by regebro on 2008-11-22
I could write a short single boot section if desired. I know it's not recommended, bit some comments could be good, because it is not always completely trivial. :)

Or I could make a separate page, and we can link to it. After all, it's just silly people like me doing something that stupid. :D

---

### Post by jrib on 2008-11-22
> **regebro said:**
> I could write a short single boot section if desired. I know it's not recommended, bit some comments could be good, because it is not always completely trivial. :)

Or I could make a separate page, and we can link to it. After all, it's just silly people like me doing something that stupid. :D

I think it makes sense to have it on that page and just explain in the introduction what the advantages and disadvantages are.  Go for it!

---

### Post by beauman on 2008-11-22
> **jrib said:**
> I've started to merge all of the installation documentation into [https://wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation](https://wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation).  I noticed that some pages do not recommend creating a swap partition.  Does anyone have any thoughts on what should be recommended?

Personally, I'm for a swap partition because I believe it's needed to be able to hibernate.  Does a swap partition cause problems with bootcamp however?

It's something with a swap file instead of partition. Haven't tried. 
There is one thing that came to my mind yesterday:

I have problems writing from Ubuntu to OS X and vice versa. The
driver for ext3 is crashing under OS X. And I like the journaling of
HFS+ to be enabled, so i can' t write from the linux side.

I thought we could maybe recommend a "transfer" partition with ntfs
or vfat32. This way both systems could write to it.

Are you going to put your pages to wiki.ubuntu.com or help.ubuntu.com?

( I have started to draw a map of our pages from wiki.ubuntu.com and the new pages at help.ubuntu.com)



friendly regards, beauman

---

### Post by beauman on 2008-12-04
[wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation]("https://wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation")

Cool!

---

### Post by pxwpxw on 2008-12-04
Yep, except that it is mandatory to install refit, otherwise you cant sync the MBR.
But I dont want to mess with the wiki.

---

### Post by cyberdork33 on 2008-12-04
> **jrib said:**
> I've started to merge all of the installation documentation into [https://wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation](https://wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation).  I noticed that some pages do not recommend creating a swap partition.  Does anyone have any thoughts on what should be recommended?

Personally, I'm for a swap partition because I believe it's needed to be able to hibernate.  Does a swap partition cause problems with bootcamp however?

That looks great. I would still recommend a swap partition, though I do not usually recommend it be 2x the amount of RAM you have anymore. I think you need at least the same size swap as you have RAM in order to have hibernate work (as the contents of RAM is dumped there for that).

---

### Post by cyberdork33 on 2008-12-04
> **pxwpxw said:**
> Yep, except that it is mandatory to install refit, otherwise you cant sync the MBR.
But I dont want to mess with the wiki.
Well, you could technically get gptsync under a LiveCD and run it, but that is a bit more cumbersome than just installing rEFIt (even temporarily).

---

### Post by beauman on 2008-12-05
> **pxwpxw said:**
> ...But I dont want to mess with the wiki.

I also think, the instructions could be revised a bit. 
I think (or hope??) it's ok to edit it.

I just tried to rezise my hfs+ partition with boot camp.
It refused to do anything, probably because I already have a second
OS installed.

Next to boot camp and the diskutil from the terminal there
is also a GUI tool called "Festplattendienstprogramm" (= harddrive
disk utility ?) Maybe it's just the frontend to the terminal version.

I haven't used it, but, if the GUI tool works perfect, maybe we should
make this program the first choice? It handels several
OSes and it's not so error prone as a terminal program. 

So I think, it would be good, if someone could revise the wiki.

---

### Post by pxwpxw on 2008-12-05
After a second look at the wiki [https://wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation](https://wiki.ubuntu.com/JasonRibeiro/AppleIntelInstallation), I think the various combinations of multi-booting setups and windows varieties could be treated as a separate issue, and should not be confused with the basic installation guide and post install issues, as in the community help Macbook [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) - that deals with a minimal Ubuntu plus Macosx multi-booting setup in an orderly fashion.
The wiki seems to be completely departing from the idea of a template and common issues, and there is inconsistent treatment of what should be common items like partitioning methods and using refit to cleanup.
In short I don't think the wiki merging approach is the right way to go.
Apologies if I offended anyone.

---

### Post by beauman on 2008-12-05
I like the page so far. It's pretty clear structured:

[LIST]
[*] Introduction
[*] OS X and Ubuntu dual boot
[*] Triple Boot Methods
[*] Troubleshooting
[*] Obtaining Help
[/LIST]

Do you mind to sketch the idea you have in mind, how this
page could look like?

Actually, I think it is some kind of a first draft.
It's just copy&paste of what we had so far. If you like
to revise it, do so.

To rEFIT: I think you are right, we should just clearly 
recommend to install it. It has lots of advantages and
no disadvantages. 

What kind of a partitioning method would you recommend to use?

Then we should also recommend the swap partition, as
cyberdork suggested.

There is also another point, we should consider: Transfering
data from one OS to the other. For my installation, I can't 
copy any data from one OS to the other. 
If we recommend to install Ubuntu in an ext2 partition,
is the MAC OS driver then guarantied to work? Or should
we recommend to use a transfer partition with vfat? Is Mac OS
capable of reading and writing ntfs? Or should we recommend
to switch of journaling under OS X? :confused:

---

### Post by beauman on 2008-12-05
I did some testing to find answers to my questions.

First, I tried to resize my HFS+ partition with **BootCamp**, that
failed, probably because I already have two additional partitions.

Then I tried **Disk Utility**, the GUI tool. It looked  nice,
it showed all my partitions and I could use the mouse to resize 
the "area" of the hfs+ partition. When I pressed the accept button,
I got an error message. 

It worked with **diskutil**:

```

beaumans-macbook:~ beauman$ ls /dev/disk*
/dev/disk0	/dev/disk0s1	/dev/disk0s2	/dev/disk0s3	/dev/disk0s4
beaumans-macbook:~ beauman$ diskutil resizeVolume disk0s2 limits
For device disk0s2 Macintosh HD:
	Current size:	80396419072 bytes
	Minimum size:	32698286080 bytes
	Maximum size:	81286201856 bytes
beaumans-macbook:~ beauman$ diskutil resizeVolume disk0s2 65G
Started resizing on disk disk0s2 Macintosh HD
Verifying
Resizing Volume
Adjusting Partitions
[ + 0%..10%..20%..30%..40%..50%..60%..70%..80%..90%..100% ] 
Finished resizing on disk disk0s2 Macintosh HD
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *149.1 Gi   disk0
   1:                        EFI                         200.0 Mi   disk0s1
   2:                  Apple_HFS Macintosh HD            64.9 Gi    disk0s2
   3:                 Linux Swap                         976.6 Mi   disk0s3
   4:       Microsoft Basic Data ibex_on_mac             73.0 Gi    disk0s4


```


[COLOR="RoyalBlue"]Conclusion ==>[/COLOR] In the wiki, we should recommend running **diskutil** in the terminal, to resize the
Mac partition. Even if it's more error-prone, but it seems to work best.



Having gained 10G of empty space on my harddrive, I created a vfat32
partition with gparted. It showed up under Ubuntu. But it did not
show up under Mac OS! I had to mount it in the terminal, just like 
pxwpxw explained [here]("http://ubuntuforums.org/showthread.php?t=1001595"):

```

$ diskutil list 
 3: Microsoft Reserved                    10.0 Gi    disk0s5
$ mkdir transfer
$ sudo mount -t msdos /dev/disk0s5 transfer

```

It then showed up on the desktop as a harddrive.
I still have to try to create the vfat partition with
diskutility, so it gets auto mounted.


[COLOR="RoyalBlue"]Conclusion ==>[/COLOR] A transfer partition
could be a way to exchange files between OS X and Ubuntu.

I also tested, if Ext2FS_1.4d4 would recognize the Ubuntu partition,
if it were ext2. So I made a backup to USB, deleted the ext3 partition
of Intrepid and re-created it using ext2. Now my Intrepid runs
on an ext2 filesystem, but Ext2FS still won't mount it.


[COLOR="RoyalBlue"]Conclusion ==>[/COLOR] It is not guarantied, that
you get read or write support for Ubuntu partitions under OS X.

---

### Post by pxwpxw on 2008-12-05
I find that a hfsplus (unjounalled) transfer partition is best between Macosx and Ubuntu, it does not have the FAT problems just discussed,

---

### Post by pxwpxw on 2008-12-06
> **beauman said:**
> I like the page so far. It's pretty clear structured:

[LIST]
[*] Introduction
[*] OS X and Ubuntu dual boot
[*] Triple Boot Methods
[*] Troubleshooting
[*] Obtaining Help
[/LIST]

Do you mind to sketch the idea you have in mind, how this
page could look like?

I had in mind this sort of purpose and scope, triggered by the numerous options identified in the wiki.

Drive partition preparation pre-installation.

Preparing the space for the Ubuntu installation.
(multi OS, partitions and partitioner options).

 Scope - matrix for all possible configurations and the partitioning mthods.
 Content - limited to current configurations and methods and what to do for each.

(MacOsx, Ubuntu, Windows)
(Bootcamp, Diskutil, disk utility, gparted, parted.)
(EFI, msdos, hfs+, hfs+journal)

Not including ubuntu linux partitioning options, swap options etc.
Not including the Ubuntu installation proper, detailed elsewhere.

Maybe a similar smaller Post install/restart version to handdle the common broken MBR sort of situation.

These would fit around the specific ubuntu/mac install guides, but be more general.

I can try to get a new page outline together, but I don't know how to drive the wiki editor yet, don't like its presentation much.
Also I am a Tiger user, non-windows, non Bootcamp, and like to start with an empty disk and the Macosx DVD Disk Utility.

---

### Post by cyberdork33 on 2008-12-06
I actually never recommend using the CLI tool as most people don't understand how to use it. DiskUtility works fine. Boot camp is quite limited, but I usually recommend it to do the initial partitioning for new users because it is simple.

---

### Post by beauman on 2008-12-07
> **cyberdork33 said:**
>  DiskUtility works fine. 

No. It's buggy. Didn't work for me. See my post above. Other people
experienced the same problems.

> **cyberdork33 said:**
>  Boot camp is quite limited, but I usually recommend it to do the initial partitioning for new users because it is simple.
Yes.

I think we should recommend BootCamp for partitioning for the first time.
For all additional partitioning  it's diskutil. It's not that hard or
error-prone to use. You can they "list" and see what partitions are hfs+. 
Then you say "limits", to verify, that you chose the right partition. Then you repartition. 

We recommend all the time in the wikis to use the terminal, so why not 
here. 


[QUOTE=pxwpxw]
I can try to get a new page outline together, but I don't know how to drive the wiki editor yet, don't like its presentation much.
[/QUOTE]

Great! And don't worry, it's a peace of cake. 

I think we should place it into the user space wikis. It is still part of the whole installation process. We focus on structuring the info,
even if we also add content.

---

### Post by pxwpxw on 2008-12-07
Just a minor point, Leopard and Tiger  have  different utilities. People are getting the idea they have to have leopard to install ubuntu.

---

### Post by beauman on 2008-12-13
Hi all!

[wiki.ubuntu.com/MactelSupportTeam/DocArchitecture]("https://wiki.ubuntu.com/MactelSupportTeam/DocArchitecture")

It does not really contain a matrix anymore on the community help page,
but thats not necessary anymore.

Please have a close look at the architecture, it means moving pages like
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) 

As always, your feedback is very appreciated.

---

### Post by cyberdork33 on 2008-12-13
> **beauman said:**
> Hi all!

[wiki.ubuntu.com/MactelSupportTeam/DocArchitecture]("https://wiki.ubuntu.com/MactelSupportTeam/DocArchitecture")

It does not really contain a matrix anymore on the community help page,
but thats not necessary anymore.

Please have a close look at the architecture, it means moving pages like
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) 

As always, your feedback is very appreciated.

the page is not editable and it is a png, not an svg. On that note, can you use a different color other than that dark blue. It makes it very difficult to read the text in the boxes.

I like the map though. It will be very useful. He are my comments:

You have the Doc Template at help.ubuntu.com. I think I understand why you placed it there, but it really is there for the team. It is not support documentation, so it should be at wiki.ubuntu.com

I like pretty much everything else about the layout, but the "touchpad fine tuning" document should be so generic that it is not Mac-specific, or be specfic, but then reside at the different hardware pages (the different macbook (pro) machines have different touchpad hardware, and thus require different parameters for tweaking).

---

### Post by beauman on 2008-12-14
> **cyberdork33 said:**
> the page is not editable and it is a png, not an svg. On that note, can you use a different color other than that dark blue. It makes it very difficult to read the text in the boxes.

Done & svg attached

> **cyberdork33 said:**
> 
I like the map though. It will be very useful. 


I'm glad to hear this. We never really talked about the pages

community/MacBook
community/MacBookPro
community/MacBookAir
community/Mac_mini
community/iMac
...

Now such a page just contains links to generic instructions and the hardware revisions. It's a big step, pages like [help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook") will look quite different. 


> **cyberdork33 said:**
> 
You have the Doc Template at help.ubuntu.com. I think I understand why you placed it there, but it really is there for the team. It is not support documentation, so it should be at wiki.ubuntu.com


At first, I placed the template [here]("https://wiki.ubuntu.com/MactelSupportTeam/DocTemplate"), but that page doesn't show up when you create a new page at help.ubuntu.com. The links to the [icon page]("https://help.ubuntu.com/community/IconsPage"), where I have uploaded the new icons, were broken. Now the former doc template page at wiki.ubuntu.com explains redirects to help.ubuntu.com.

> **cyberdork33 said:**
> 
I like pretty much everything else about the layout, but the "touchpad fine tuning" document should be so generic that it is not Mac-specific, or be specfic, but then reside at the different hardware pages (the different macbook (pro) machines have different touchpad hardware, and thus require different parameters for tweaking).

It's up to the group to find out for what hardware the "offset" of creating just an other sub-wiki pays off. I did some  investigation on MacTracker and the results are [on the team page]("https://wiki.ubuntu.com/MactelSupportTeam#Similar/almost%20identical%20hardware"). This point has to be more elaborated.

---

### Post by beauman on 2008-12-14
@jason and pxwpxw: I copied the basic installation instructions to [help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation")

I updated the [ToDo-List]("https://wiki.ubuntu.com/MactelSupportTeam#Todo%20List%20Mactel-Support%20Team") and started a [list]("https://wiki.ubuntu.com/MactelSupportTeam#List%20with%20pages%20to%20be%20deleted") with pages to be deleted.


I think, that all pages like [the guidelines]("https://wiki.ubuntu.com/MactelSupportTeam/DocGuidlines"), the [team page]("https://wiki.ubuntu.com/MactelSupportTeam#Creating%20a%20new%20page"), the [doc architecture]("https://wiki.ubuntu.com/MactelSupportTeam/DocArchitecture") and the [doc template]("https://help.ubuntu.com/community/MactelSupportTeam/DocTemplate") should now be up-to-date with our naming scheme.

Does anybody know, how we can move [wiki.ubuntu.com/MacBook/SantaRosa]("https://wiki.ubuntu.com/MacBook/SantaRosa") to [help.ubuntu.com/community/MacBook4-1/Intrepid]("https://help.ubuntu.com/community/MacBook4-1/Intrepid") with preserving the history?

---

### Post by cyberdork33 on 2008-12-15
> **beauman said:**
> At first, I placed the template [here]("https://wiki.ubuntu.com/MactelSupportTeam/DocTemplate"), but that page doesn't show up when you create a new page at help.ubuntu.com. The links to the [icon page]("https://help.ubuntu.com/community/IconsPage"), where I have uploaded the new icons, were broken. Now the former doc template page at wiki.ubuntu.com explains redirects to help.ubuntu.com.OK, I see what you are trying to do. I did not know about the Icon Page, though you should be able to place the full URL to link instead of the short wiki format...
I also came across this when checking it out:
[https://help.ubuntu.com/community/DocumentationTemplate](https://help.ubuntu.com/community/DocumentationTemplate)

I think we just try to conform to this as much as we can too (It is pretty generic, and I think our template is already OK, so no changes may be needed).

> **beauman said:**
> Does anybody know, how we can move [wiki.ubuntu.com/MacBook/SantaRosa]("https://wiki.ubuntu.com/MacBook/SantaRosa") to [help.ubuntu.com/community/MacBook4-1/Intrepid]("https://help.ubuntu.com/community/MacBook4-1/Intrepid") with preserving the history?
I don't think it can be done.

---

### Post by beauman on 2008-12-16
I updated  [MacBook]("https://help.ubuntu.com/community/MacBook") and [MacBookPro]("https://help.ubuntu.com/community/MacBookPro") to conform with the new documentation structure. 

I copied the former content (preserving the history) to the right places.

Further,  for the MB & MBP, I  installed the pages where to select the Ubuntu version.

---

### Post by hyperboloid on 2008-12-16
> **beauman said:**
> I updated  [MacBook]("https://help.ubuntu.com/community/MacBook") and [MacBookPro]("https://help.ubuntu.com/community/MacBookPro") to conform with the new documentation structure. 

I copied the former content (preserving the history) to the right places.

Further,  for the MB & MBP, I  installed the pages where to select the Ubuntu version.

Oops!  Now we seem to have lost the old pages, which contained a wealth of useful information. For instance, the link [https://help.ubuntu.com/community/MacBookPro]("https://help.ubuntu.com/community/MacBookPro") used to take you to a very long and comprehensive article, which has now been replaced by something with almost no content (but good structure). 

If you are going to destroy existing links, shouldn't there be someway to preserve the old content, at least during the transition? Or am I missing something obvious?

---

### Post by beauman on 2008-12-17
I deleted them. Muahahahahah!!! :evil:





(Just joking)

> **beauman said:**
> 

I copied the former content (preserving the history) to the right places.



The original pages are now split into first and second generation wikis, like the [DocGuidlines]("https://wiki.ubuntu.com/MactelSupportTeam/DocGuidlines") recommend. 


[LIST]
[*][history of MacBook1-1/Hardy (original MacBook page)]("https://help.ubuntu.com/community/MacBook1-1/Hardy?action=info")
[*] and for the 2nd generation MacBook: [MacBook2-1/Hardy]("https://help.ubuntu.com/community/MacBook2-1/Hardy")
[*][history of MacBookPro1-1_1-2/Intrepid (original MacBookPro page)]("https://help.ubuntu.com/community/MacBookPro1-1_1-2/Intrepid?action=info")
[*] and for the 2nd generation MacBookPro: [MacBookPro2-1_2-2/Intrepid]("https://help.ubuntu.com/community/MacBookPro2-1_2-2/Intrepid")
[/LIST]

I am going to place a hint, so other people who didn't follow our discussion here, know where to find the content they expect from [MacBook]("https://help.ubuntu.com/community/MacBook") and [MacBookPro]("https://help.ubuntu.com/community/MacBookPro").

I  think, the new structure really rocks. The confusion about the right MB / MBP wiki should finally be over! I told you, it's a big step, but now it's done. :p

The entry point [MactelSupportTeam/CommunityHelpPages]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages") still needs some revision though. This page should only contain links to the product pages [MacBook]("https://help.ubuntu.com/community/MacBook"), [MacBookPro]("https://help.ubuntu.com/community/MacBookPro"), [MacBookAir]("https://help.ubuntu.com/community/MacBookAir"), [iMac]("https://help.ubuntu.com/community/iMac"), [MacPro]("https://help.ubuntu.com/community/MacPro"), [Mac_mini]("https://help.ubuntu.com/community/Mac_mini") and [xServe]("https://help.ubuntu.com/community/xServe"). 

Or would you still like to have a matrix there, linking like we talked about? I wouldn't place it there anymore, because 
[LIST]
[*]**The new structure speaks for it self**. No need for additional linking.
[*]**Things get too complicated**, even for the wiki writers. It's enough to place and install the wiki at one location. (Example: If you write a wiki for MBP 4,1 for Jaunty, you have to create a new page [MacBookPro4-1/Jaunty]("https://help.ubuntu.com/community/MacBookPro4-1/Jaunty") and make an entry in [MacBookPro4-1]("https://help.ubuntu.com/community/MacBookPro4-1"). If a new hardware model comes out, like MB 6-1 for example,  a new Ubuntu-version-page has to be created in addition ([MacBookPro6-1]("https://help.ubuntu.com/community/MacBookPro6-1")), next to the wiki ([MacBookPro6-1/Jaunty]("https://help.ubuntu.com/community/MacBookPro6-1/Jaunty")) it self.) It is quite a big challenge  for the wiki writers already.)
[*]It works like a wizard: [LIST]
[*]First page: welcome, FAQ, link to Mac products. (nothing about hw revisions). 
[*]Second page: hardware page, find the right hw revision.
[*]Third page: choose the Ubuntu version you like to install
[/LIST] The matrix would be a shortcut to the ''wizard''. But we want the user to go through the ''wizard'', where the user gets informed about hw revision and other important stuff **in a very clear-structured way**.
[/LIST]

---

### Post by hyperboloid on 2008-12-17
I confess that this thread got so complex that I stopped following it at some point, but now I see what you have in mind. The structure is sensible, and indeed speaks for itself. 

Unfortunately, the new structure also introduces new (hopefully temporary) confusion. That is an inevitable part of any change, I suppose. For example, a new user trying to install Hardy will get the impression that there is NO documentation available, when in fact much of the existing wiki content was written originally for Hardy. Wouldn't it have been more useful to preserve the Hardy info and make new pages for Intrepid, rather than update the Hardy pages to Intrepid? 

Another confusion, for example, is that some pages contain generic information that applies not only to the model listed, but also to many other models. For example, the page [https://help.ubuntu.com/community/MacBookPro1-1_1-2/Intrepid]("https://help.ubuntu.com/community/MacBookPro1-1_1-2/Intrepid") has a wealth of information about installation that applies not only to MacBook Pro 1,1 and 1,2 but also other MacBookPro models as well as MacBooks, too. Are there plans to move such content to a more generic position in the wiki structure? 

I'm wondering about the last point because I recently wrote the MBP 4,1 Intrepid wiki, putting in links to the above page, and now those links don't work anymore. Before I update them, I'd like to know if the links are going to change again soon.

---

### Post by cyberdork33 on 2008-12-17
> **hyperboloid said:**
> Oops! Now we seem to have lost the old pages, which contained a wealth of useful information.
That article was a little too long and comprehensive. It had a lot of repeated information, information for more than one MacbookPro version, information that was not specific to MacBookPro, etc. If there is something that you think was vital in the old page, please check the history, find the content and add it to its appropriate, organized location. Basically, all the documentation pages were quite messy and confusing, and we are attempting to cleanup and organize a little better.

> **beauman said:**
> Or would you still like to have a matrix there, linking like we talked about? I wouldn't place it there anymore, because
while the information is presented in a manner that you can (eventually) find the page you need, I think that it is getting a little too deep:

documentation matrix > macbook page > macbook version-specific page > Macbook version-specific, ubuntu version-specific page

This is too many clicks. This is why I had earlier suggested making the " macbook version-specific" page contain the documentation for the current Ubuntu release, and when a new Ubuntu release is made, it is archived in a /versionname subpage.

Also, how did you move the page and preserve the history?

> **hyperboloid said:**
> For example, a new user trying to install Hardy will get the impression that there is NO documentation available, when in fact much of the existing wiki content was written originally for Hardy. Wouldn't it have been more useful to preserve the Hardy info and make new pages for Intrepid, rather than update the Hardy pages to Intrepid? Well, in the past there was really only one page that was continually morphed to support the latest release of Ubuntu, so it actually should be worse with the old format (as eventually, the Hardy-specific stuff does, indeed dissapear). With this new format, the MacBookPro1,1 documentation for Hardy should now be at the Macbookpro1-1/Hardy subpage. If it is not there already, then it probably should be migrated there.

> **hyperboloid said:**
> Another confusion, for example, is that some pages contain generic information that applies not only to the model listed, but also to many other models. For example, the page [https://help.ubuntu.com/community/MacBookPro1-1_1-2/Intrepid](https://help.ubuntu.com/community/MacBookPro1-1_1-2/Intrepid) has a wealth of information about installation that applies not only to MacBook Pro 1,1 and 1,2 but also other MacBookPro models as well as MacBooks, too. Are there plans to move such content to a more generic position in the wiki structure?
Some yes. The [AppleiSight page]("https://help.ubuntu.com/community/AppleiSight") for example is common for many Macs, (and there is a generic installation page now too I think). I don't think it is desirable to put EVERYTHING in it's own page like that though, as it is simply another link to follow and another page to read.

> **hyperboloid said:**
> I'm wondering about the last point because I recently wrote the MBP 4,1 Intrepid wiki, putting in links to the above page, and now those links don't work anymore. Before I update them, I'd like to know if the links are going to change again soon.I would avoid cross-linking to other version's pages as it might be confusing to the user which page they should ulitimately be following. On the other hand, if there is something that is common between many Macs, then create a new page that can be linked to by both version's pages (like the [AppleiSight page]("https://help.ubuntu.com/community/AppleiSight")).

---

### Post by beauman on 2008-12-17
> **hyperboloid said:**
>  
For example, a new user trying to install Hardy will get the impression that there is NO documentation available, when in fact much of the existing wiki content was written originally for Hardy. Wouldn't it have been more useful to preserve the Hardy info and make new pages for Intrepid, rather than update the Hardy pages to Intrepid? 


We preserve all information, the only thing we loose is the wiki history, when we move pages from wiki.ubuntu.com to help.ubuntu.com. (For example [wiki.ubuntu.com/MacBook/SantaRosa]("https://wiki.ubuntu.com/MacBook/SantaRosa") -> [help.ubuntu.com/community/MacBook3-1/Intrepid]("https://help.ubuntu.com/community/MacBook3-1/Intrepid"))

Also, we create new pages for all wikis, Hardy and Intrepid. The **product pages** "MacBook" and "MacBookPro" are Ubuntu-version independent. 

It would be very good, if someone could go through the pages related to Hardy (for example [MacBookPro_Penryn]("https://help.ubuntu.com/community/MacBookPro_Penryn")), clean hints about Intrepid and move them to the new naming scheme.

> **hyperboloid said:**
>  
Another confusion, for example, is that some pages contain generic information that applies not only to the model listed, but also to many other models. For example, the page [https://help.ubuntu.com/community/MacBookPro1-1_1-2/Intrepid]("https://help.ubuntu.com/community/MacBookPro1-1_1-2/Intrepid") has a wealth of information about installation that applies not only to MacBook Pro 1,1 and 1,2 but also other MacBookPro models as well as MacBooks, too. Are there plans to move such content to a more generic position in the wiki structure? 


Definitely! JRib started a [page about generic installation instructions]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation") and pxwpxw is going to revise them. The install part is way too long in [MacBookPro1-1_1-2/Intrepid]("https://help.ubuntu.com/community/MacBookPro1-1_1-2/Intrepid").

Have a look at the [working matrix]("https://wiki.ubuntu.com/MactelSupportTeam#Hardware/Software/Contributors%20Working%20Matrix%20(Ubuntu%208.10%20%22Intrepid%20Ibex%22)"), it is scheduled to be cleaned. Feel free to use the matrix, if you notice, that something in a wiki could be improved, but you don't like to do it right now!


> **hyperboloid said:**
>  
I'm wondering about the last point because I recently wrote the MBP 4,1 Intrepid wiki, putting in links to the above page, and now those links don't work anymore. Before I update them, I'd like to know if the links are going to change again soon.

Well, actually, we have to discuss the subject "sub-wiki" a bit more. It is already shown, in the doc overview. But we still have to find out, for what hw the same wikis will work. 

The basic installation instructions are fixed, though, you can link them.

---

### Post by beauman on 2008-12-17
> **cyberdork33 said:**
> 

Also, how did you move the page and preserve the history?



You can copy the pages, preserving the history, within help.ubuntu.com
with the drop-down menu.

Ok then, no matrix on the entry point. Good.

The other question:

Now we have three clicks to go to the wiki, all of them make sense:
[LIST=1]
[*]Mac Product
[*]Hardware Revision
[*]Ubuntu Version
[/LIST]

Do you still think, that we should assume that the user wants to install the latest version? I think, the way we have it right now is straight-forward. I think there are a lot of people out there, who are not updating every six month and who prefere the LTS. So it is awkward  for them to find the right wiki. And moving an "old" page is also always a bit complicated. The doc overview, that you approved lately,  also shows the structure as it is now the case. I like it better the way it is right now, but we can of course change it, if you like to.

---

### Post by cyberdork33 on 2008-12-17
> **beauman said:**
> Ok then, no matrix on the entry point. Good.
No I think the matrix is good, I think that the matrix should have links to the different hardware versions directly, skipping the generic /Macbook, /MacbookPro, etc general pages. The general pages are there so if someone just searches for "Macbook" in the wiki, the information is there to find the page for their specific version.


> **beauman said:**
> Do you still think, that we should assume that the user wants to install the latest version?
Yes, always. Honestly, it is misunderstood what LTS is for. LTS refers to commercial support from canonical, if you are not running a commercial system such as a server, there is no reason to worry about using an LTS version unless you just don't want to update.

---

### Post by beauman on 2008-12-18
> **cyberdork33 said:**
> 

while the information is presented in a manner that you can (eventually) find the page you need, I think that it is getting a little too deep:

documentation matrix > macbook page > macbook version-specific page > Macbook version-specific, ubuntu version-specific page



Now all wikis are one click away from the entry point: 

documentation matrix > wiki Mac-product-hardware-revision-specific, Ubuntu-version-specific page

See [MactelSupportTeam/CommunityHelpPages]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")


> **cyberdork33 said:**
> 

... This is why I had earlier suggested making the " macbook version-specific" page contain the documentation for the current Ubuntu release, and when a new Ubuntu release is made, it is archived in a /versionname subpage.


I changed  [community/MacBook3-1]("https://help.ubuntu.com/community/MacBook3-1"),  [community/MacBook4-1]("https://help.ubuntu.com/community/MacBook4-1") and  [community/MacBook5-1]("https://help.ubuntu.com/community/MacBook5-1"), and left [community/MacBook1-1]("https://help.ubuntu.com/community/MacBook1-1") and [community/MacBook2-1]("https://help.ubuntu.com/community/MacBook2-1") as they were.

**Only the first three** automatically redirect to the Ubuntu version we recommend, say Intrepid. This is the behavior you asked for, but there is no later moving required. 

We have to keep things simple, even for the wiki writers. For us, the new naming scheme is clear, but for others it will take some time.** Moving wikis can't be part of our structure**. People normally don't do such things.


For MB1-1 and MB2-1 there is no Intrepid wiki, the pages do not automatically redirect. Also, if a **new Ubuntu version** comes out, we are going to recommend from the first day on the new version, while  the corresponding wiki may not exist yet or is empty. So for this period of time, we should **switch off automatically redirecting**.

I also moved the content of the *revision-pages* (like MacBook1-1/, etc.) to the *product page*: [MacBook]("https://help.ubuntu.com/community/MacBook"). I like to know, if you like it.

---

### Post by beauman on 2008-12-18
Please move your wikis to the right locations and create the product and revision pages. Sign them in at the start page. You can use the copy function from the drop-down-menu at [community/MacBook3-1]("https://help.ubuntu.com/community/MacBook3-1?action=show") and [community/MacBookPro]("https://help.ubuntu.com/community/MacBookPro"). Thanx!


@ cyberdork: You have a nice intro at your page for the mactel installation. Do you like to integrate it into our start page? :)

---

### Post by cyberdork33 on 2008-12-19
> **beauman said:**
> Now all wikis are one click away from the entry point: 

documentation matrix > wiki Mac-product-hardware-revision-specific, Ubuntu-version-specific page

See [MactelSupportTeam/CommunityHelpPages]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")yes, but you were talking about removing the version matrix (at least that's what it sounded like...) I like it the way it is now.



> **beauman said:**
> I changed  [community/MacBook3-1]("https://help.ubuntu.com/community/MacBook3-1"),  [community/MacBook4-1]("https://help.ubuntu.com/community/MacBook4-1") and  [community/MacBook5-1]("https://help.ubuntu.com/community/MacBook5-1"), and left [community/MacBook1-1]("https://help.ubuntu.com/community/MacBook1-1") and [community/MacBook2-1]("https://help.ubuntu.com/community/MacBook2-1") as they were.

**Only the first three** automatically redirect to the Ubuntu version we recommend, say Intrepid. This is the behavior you asked for, but there is no later moving required. 
Excellent! I think that is a much better plan. The top level page only needs to have the redirect changed when the new Ubuntu version is released. 

> **beauman said:**
> We have to keep things simple, even for the wiki writers. For us, the new naming scheme is clear, but for others it will take some time.** Moving wikis can't be part of our structure**. People normally don't do such things. understood, though I wouldn't think of it as "moving" as much as I would "archiving". I think the way you are redirecting now though solves the issue anyway.

> **beauman said:**
> For MB1-1 and MB2-1 there is no Intrepid wiki, the pages do not automatically redirect. Also, if a **new Ubuntu version** comes out, we are going to recommend from the first day on the new version, while  the corresponding wiki may not exist yet or is empty. So for this period of time, we should **switch off automatically redirecting**.Yes I was just thinking about this when responding to the above. Each Ubuntu version page should probably have a link to the previous version page (and LTS page, maybe). Also, I wouldn't expect the Jaunty page to be empty on the day Jaunty is released. Many people will be running Jaunty well before release day and will have an idea of things that need to be fixed for installers on day-0 and can add this information to a Jaunty page before it is even released. I would expect a bit of the previous releases' info to copy over (with some modifications for changes) or be removed completely (because it now works out-of-the-box).

> **beauman said:**
> I also moved the content of the *revision-pages* (like MacBook1-1/, etc.) to the *product page*: [MacBook]("https://help.ubuntu.com/community/MacBook"). I like to know, if you like it.Yes that is good because I am sure that people will be googling "Ubuntu on Macbook" or something and that page will come up. I also like your version of "how to find your mac version" better.

> **beauman said:**
> @ cyberdork: You have a nice intro at your page for the mactel installation. Do you like to integrate it into our start page? :)I do not know what page you are referring to... you mean on my blog?

---

### Post by beauman on 2008-12-19
Yeah! That sounds very positive! So we are getting closer to our goals. :)

> **cyberdork33 said:**
> yes, but you were talking about removing the version matrix (at least that's what it sounded like...) I like it the way it is now. Yes. I thought the structure you proposed is speaking for itself, so we don't need it anymore. But it's nice to have it of course.

> **cyberdork33 said:**
> 
I do not know what page you are referring to... you mean on my blog?
Yes. It is not so stiff like the short intro we have right now. But you don't have to do this, just if you like to. We have so many new group members, I am sure somebody will do it. It would be good, if a native english speaker would write it, so it has the decency a start page should have.

I am going to update the doc overview with the matrix and the "default link" to the latest distro.

---

### Post by cyberdork33 on 2008-12-19
> **beauman said:**
> Yes. It is not so stiff like the short intro we have right now. But you don't have to do this, just if you like to. We have so many new group members, I am sure somebody will do it. It would be good, if a native english speaker would write it, so it has the decency a start page should have.

well, I would gladly use something I wrote, but I still really don't know what you are referring to... Can you post a link? (You can PM me), or are you asking me to write something new?

---

### Post by beauman on 2008-12-19
I was talking about your blog entry from the 16th December. I liked the way how you explain, that it's simple on the one hand, but also different to the usual procedure. Your intro is encouraging, but the reader does not get the impression that the install is trivial...

---

### Post by cyberdork33 on 2008-12-19
> **beauman said:**
> I was talking about your blog entry from the 16th December. I liked the way how you explain, that it's simple on the one hand, but also different to the usual procedure. Your intro is encouraging, but the reader does not get the impression that the install is trivial...Oh, you mean the installation instructions. Yea I can do that, though it is a bit limited in that it really focuses on dual-booting only.

I will integrate it into the Installation wiki. and develop a section for single-booting Ubuntu also as that is not well covered.

EDIT: OK, I made some major mods to the page.

---

### Post by beauman on 2008-12-19
Oh, that was a  misunderstanding.

> **beauman said:**
> 

@ cyberdork: You have a nice intro at your page for the mactel installation. Do you like to integrate it into our start page? :)

I was just talking about an introduction on the start page. :)

But of course it's really great that you improve the generic install page! Cool that we get a section on single booting Ubuntu!!

---

### Post by hyperboloid on 2008-12-22
Does anyone know how to get comments to display in a code block in an Ubuntu Wiki? For example, if I type 
```

{{{
#!/bin/bash
printf "Hello World"
}}}

```
in a Wiki page, then only the second line of the script is displayed. The first line (comment line of the script) is taken by the parser to be a Wiki comment, and not displayed. (One would think that a "verbatim" code displayer would display everything ... verbatim, just like this Forum editor does.) 

This is extremely annoying behavior, since it means that it is impossible to completely display any script on an Ubuntu Wiki! :confused:

Anybody know of a workaround? Or am I missing something obvious? I've looked at all the documentation on editing Wikis, but found no joy.

---

### Post by cyberdork33 on 2008-12-22
> **hyperboloid said:**
> Does anyone know how to get comments to display in a code block in an Ubuntu Wiki? For example, if I type 
```

{{{
#!/bin/bash
printf "Hello World"
}}}

```
in a Wiki page, then only the second line of the script is displayed. The first line (comment line of the script) is taken by the parser to be a Wiki comment, and not displayed. (One would think that a "verbatim" code displayer would display everything ... verbatim, just like this Forum editor does.) 

This is extremely annoying behavior, since it means that it is impossible to completely display any script on an Ubuntu Wiki! :confused:

Anybody know of a workaround? Or am I missing something obvious? I've looked at all the documentation on editing Wikis, but found no joy.

It seems to be the # and ! combo that does it for me, but I'd say that it is probably a bug in the parser.

---

### Post by jpugh on 2008-12-26
Macbook PRO 3,1 docs.

I don't want to edit the doc directly as it may pertain to other hardware included in various 3,1 versions???
[http://help.ubuntu.com/community/MacBookPro3-1/Intrepid](http://help.ubuntu.com/community/MacBookPro3-1/Intrepid)

For instance:
-iSight works with no changed needed
-Sound works with no changes needed, however sound starts muted initially
-desktop effects - spelling - NVIDIA
-Keyboard functions - do you need hal-applesmc or applesmc-dkms? Neither works
-sensors wants applesmc-dkms???
-modprobe command for mbp-nvidia-bl is incorrect - should be "sudo modprobe mbp-nvidia-bl"
-my touchpad is appletouch not bcm5974???

This left me confused - I don't want to go and willy-nilly change things...but how do we go about corrections and/or specific hardware discrepancies?

---

### Post by jpugh on 2008-12-26
Now I found why the diff's....

Seems the page was copied from a 4,1 intrepid install...

---

### Post by hanzomon4 on 2008-12-27
> **jpugh said:**
> Macbook PRO 3,1 docs.

I don't want to edit the doc directly as it may pertain to other hardware included in various 3,1 versions???
[http://help.ubuntu.com/community/MacBookPro3-1/Intrepid](http://help.ubuntu.com/community/MacBookPro3-1/Intrepid)

For instance:
-iSight works with no changed needed
-Sound works with no changes needed, however sound starts muted initially
-desktop effects - spelling - NVIDIA
-Keyboard functions - do you need hal-applesmc or applesmc-dkms? Neither works
-sensors wants applesmc-dkms???
-modprobe command for mbp-nvidia-bl is incorrect - should be "sudo modprobe mbp-nvidia-bl"
-my touchpad is appletouch not bcm5974???

This left me confused - I don't want to go and willy-nilly change things...but how do we go about corrections and/or specific hardware discrepancies?

Word. I thought I was losing my mind for a 2nd

---

### Post by hyperboloid on 2008-12-27
> **jpugh said:**
> Now I found why the diff's....

Seems the page was copied from a 4,1 intrepid install...

Yes, someone must have copied that page into 3,1 by error. Whoever made this mistake should correct it.  

The original page for MacbookPro 3,1 is the older "Santa Rosa" page at [https://help.ubuntu.com/community/MacBookPro_SantaRosa]("https://help.ubuntu.com/community/MacBookPro_SantaRosa"). Unfortunately, that page does not even appear on the matrix, so it is unlikely that people are going to find it. Anyway, that page is more likely to apply to the MBP 3,1 even for Intrepid.

The documentation is still in transition, and things are still a bit of a mess, it seems. Someone running Intrepid on a 3,1 still needs to make a valid page about it.

---

### Post by cyberdork33 on 2008-12-28
If changes need to be made, then just make them... That is what a wiki is for. If a mistake was made when creating the page and you have access to better information, just toss the wrong stuff and put the stuff that worked in there.

---

### Post by jrib on 2008-12-31
First, thank you to everyone working on the documentation.  It is a big improvement in terms of organization from its previous state.

While browsing the current documentation, I felt as though the documentation was now broken up into too many pieces.  They make logical sense, but a lot of the pages contain the same exact contents.  I think it would be advantageous to keep very similar pages as a single page (MacBook 3.1 and 4.1 are an obvious example).  At the moment, if a new user wants to contribute a change that affects 3.1 and 4.1, he needs to edit both pages which means more work.  This is a barrier to new user contributions.  Even if there is a small difference between 3.1 and 4.1, two separate sections on the same page would be a better solution than creating two separate pages.  Only if instructions vary greatly should pages be split.

That's my two cents.  Just looking for some feedback.

And Happy New Year everyone!

---

### Post by jrib on 2008-12-31
> **hyperboloid said:**
> Does anyone know how to get comments to display in a code block in an Ubuntu Wiki? For example, if I type 
```

{{{
#!/bin/bash
printf "Hello World"
}}}

```
in a Wiki page, then only the second line of the script is displayed. The first line (comment line of the script) is taken by the parser to be a Wiki comment, and not displayed. (One would think that a "verbatim" code displayer would display everything ... verbatim, just like this Forum editor does.) 

This is extremely annoying behavior, since it means that it is impossible to completely display any script on an Ubuntu Wiki! :confused:

Anybody know of a workaround? Or am I missing something obvious? I've looked at all the documentation on editing Wikis, but found no joy.

moin thinks you are specifying the "/bin/sh" parser as in [http://moinmo.in/HelpOnParsers](http://moinmo.in/HelpOnParsers).  Workaround:
```

{{{#!plain
#!/bin/sh
hello world
}}}

```

---

### Post by jpugh on 2009-01-01
> **jrib said:**
> First, thank you to everyone working on the documentation.  It is a big improvement in terms of organization from its previous state.

While browsing the current documentation, I felt as though the documentation was now broken up into too many pieces.  They make logical sense, but a lot of the pages contain the same exact contents.  I think it would be advantageous to keep very similar pages as a single page (MacBook 3.1 and 4.1 are an obvious example).  At the moment, if a new user wants to contribute a change that affects 3.1 and 4.1, he needs to edit both pages which means more work.  This is a barrier to new user contributions.  Even if there is a small difference between 3.1 and 4.1, two separate sections on the same page would be a better solution than creating two separate pages.  Only if instructions vary greatly should pages be split.


I agree it is getting better (although the only updates really needed were for new hw and sw versions, IMHO).

I do not agree that similiar pages should be the same, for instance, MB 3,1 and 4,1 are quite different - NICs, keypads, etc are different requiring different tweaks for various tastes.

We need to have sections in the wiki for all supported versions of Ubuntu as well as all intel mac hw variants. This makes the pages more searchable, simpler to read/manage and better all around.

---

### Post by ercoppa on 2009-01-28
Some question on my behaviour in editing [this page]("https://help.ubuntu.com/community/MacBook5-1/Intrepid"):
- if I have to install the nvidia driver from the restricted tool, what icon do I have to choose? 'works with remarks' or 'manual install'?
- if I have to install a external package (for example from Mactel PPA), 'works with remarks' or 'manual install'?
- is there a page (from the other page on MB or MBP) to take as "model" (complete page with correct schema/style)?

Greets, ercoppa.

---

### Post by cyberdork33 on 2009-01-28
> **ercoppa said:**
> Some question on my behaviour in editing [this page]("https://help.ubuntu.com/community/MacBook5-1/Intrepid"):
- if I have to install the nvidia driver from the restricted tool, what icon do I have to choose? 'works with remarks' or 'manual install'?
- if I have to install a external package (for example from Mactel PPA), 'works with remarks' or 'manual install'?
- is there a page (from the other page on MB or MBP) to take as "model" (complete page with correct schema/style)?

Greets, ercoppa.
[https://wiki.ubuntu.com/MactelSupportTeam#How%20to%20create%20a%20Mactel%20wiki](https://wiki.ubuntu.com/MactelSupportTeam#How%20to%20create%20a%20Mactel%20wiki)

There is a link to the structure, guidelines, and a template.

---

### Post by beauman on 2009-01-29
> **ercoppa said:**
> Some question on my behaviour in editing [this page]("https://help.ubuntu.com/community/MacBook5-1/Intrepid"):
- if I have to install the nvidia driver from the restricted tool, what icon do I have to choose? 'works with remarks' or 'manual install'?
- if I have to install a external package (for example from Mactel PPA), 'works with remarks' or 'manual install'?
- is there a page (from the other page on MB or MBP) to take as "model" (complete page with correct schema/style)?

Greets, ercoppa.

I would say, "manual install" could be used, if you have to use the terminal or edit sys-files. 

i wonder, what the "confirmed" labels in the mbp5-1 wiki mean or what the definition of "confirmed" is. 10 useres who see the same behavior? or 100?

---

### Post by buntuLo on 2009-01-30
dear all,

i'd like to ask the few of you with experience with MacBook Pro 5.1 and (Gnome) Ubuntu to check my contribution to the page

 [https://help.ubuntu.com/community/MacBookPro5-1/Intrepid](https://help.ubuntu.com/community/MacBookPro5-1/Intrepid)

and make the appropriate changes in case any issue described there is not correct in case of Gnome desktop manager.

i'm sure that other issues about this hardware are already solved (e.g. external display and iSight cam, as reported in the old Macbook Aluminium page), but i didn't test them already, hence i don't feel confident to add them yet. hope to do it asap.

thanks and greetings, Lo.

---

### Post by cyberdork33 on 2009-01-30
> **buntuLo said:**
> i'm sure that other issues about this hardware are already solved (e.g. external display and iSight cam, as reported in the old Macbook Aluminium page), but i didn't test them already, hence i don't feel confident to add them yet. hope to do it asap.
I believe that the iSight should work out-of-the-box with no configuration. run 'gstreamer-properties' and check the video tab to test it.

I also looked over the page and made some formatting changes and changed some of the links to point to the same information, but on the common page for all macs.

---

### Post by buntuLo on 2009-01-30
> **cyberdork33 said:**
> I believe that the iSight should work out-of-the-box with no configuration. run 'gstreamer-properties' and check the video tab to test it.
I also looked over the page and made some formatting changes and changed some of the links to point to the same information, but on the common page for all macs.

CD33 Note: I think that they do indeed work, they are just different keys than under Gnome. PLease someone verify. 

correct! tested the iSight with Skype, it works out of-the-box.

about the function keys, there's a way to configure them in kde, but they do not work properly: some of them are not detected as input, hence cannot be configured; others are detected and configured, but a few do not work. more specific: brightness down sometimes works, but up does not. volume up/down work, while mute only shows the tooltip with the current volume. i didn't manage to find a way to map eject. dashboard isn't detected. i suspect that there might be problems with the keyboard layout, but after trying them all i had to give up.

thanks for editing back the page! Lo.

---

### Post by SnaeDelarj on 2009-02-15
I'm a little bit confused if this is the right place to post.

I just installed Ubuntu 8.10 Intrepid on my MacBook 2,1. Nearly everything works out of the box and the Mactel Community Help and Wiki Pages have been a great guideline for the tweaks I did.

There's one thing I would like to add to [https://help.ubuntu.com/community/MacBook2-1/Intrepid](https://help.ubuntu.com/community/MacBook2-1/Intrepid)

Sound was working on my internal speakers, but it was very quiet and sounded thin. I read about MacBook 3,1 owners who encountered the same problem possibly due to the ALSA Driver that doesn't detect the 3rd mid-range internal speaker.
But MacBooks 3,1 use the Intel ICH8 chipsets with 82801H High Definition Audio while MacBooks 2,1 use Intel 82801G (ICH7 Family) High Definition Audio. 

I solved the problem by right-clicking (F12 is the default key under Ubuntu, if you didn't activate right-clicking with the trackpad or another key) on the Volume Control Panel -> Open Volume Control -> Choose the default HDA Intel (Alsa mixer) -> Preferences. Select the Surround track to be visible. Back in the mixer turn the surround track on and the mid-frequency speaker will turn on.

You now have the sound "quality" you may know from Mac OS X running on your MacBook.

If there is a way to have the surround track turned on by default when you install the next release of Ubuntu (Jaunty) on a MacBook, that would be great, preventing some people from spreading the rumour that "MacOSX is better sounding than Ubuntu".

Well, maybe I'm the only one who had trouble to find out this simple solution, or it's already solved but not documented...

Did someone else with a MacBook 2,1 have the same problem?
Does it even help with MacBook 3,1 to solve the sound issue?

If anyone could approve this, I could rewrite this and add it to the wiki if thats appropriate.

Thanks for reading.

---

### Post by cyberdork33 on 2009-02-15
> **SnaeDelarj said:**
> I'm a little bit confused if this is the right place to post.

I just installed Ubuntu 8.10 Intrepid on my MacBook 2,1. Nearly everything works out of the box and the Mactel Community Help and Wiki Pages have been a great guideline for the tweaks I did.

There's one thing I would like to add to [https://help.ubuntu.com/community/MacBook2-1/Intrepid](https://help.ubuntu.com/community/MacBook2-1/Intrepid)

Sound was working on my internal speakers, but it was very quiet and sounded thin. I read about MacBook 3,1 owners who encountered the same problem possibly due to the ALSA Driver that doesn't detect the 3rd mid-range internal speaker.
But MacBooks 3,1 use the Intel ICH8 chipsets with 82801H High Definition Audio while MacBooks 2,1 use Intel 82801G (ICH7 Family) High Definition Audio. 

I solved the problem by right-clicking (F12 is the default key under Ubuntu, if you didn't activate right-clicking with the trackpad or another key) on the Volume Control Panel -> Open Volume Control -> Choose the default HDA Intel (Alsa mixer) -> Preferences. Select the Surround track to be visible. Back in the mixer turn the surround track on and the mid-frequency speaker will turn on.

You now have the sound "quality" you may know from Mac OS X running on your MacBook.

If there is a way to have the surround track turned on by default when you install the next release of Ubuntu (Jaunty) on a MacBook, that would be great, preventing some people from spreading the rumour that "MacOSX is better sounding than Ubuntu".

Well, maybe I'm the only one who had trouble to find out this simple solution, or it's already solved but not documented...

Did someone else with a MacBook 2,1 have the same problem?
Does it even help with MacBook 3,1 to solve the sound issue?

If anyone could approve this, I could rewrite this and add it to the wiki if thats appropriate.

Thanks for reading.
You do not need approval from anyone to add such information. If you think it is helpful to MacBook2,1 Intrepid Users, then add it. If you think that it should be on by default in Jaunty, please first test Jaunty on your hardware to check that the change still needs to be made, and if so, then file a bug in launchpad.

---

### Post by mirkop on 2009-02-18
Hi all!
I'm a quite long time Ubuntu user (for work, study and "fun" stuff) and I've found always the right answer in MactelSupport pages ;)
Now I'm running with success (K)Ubuntu 9.04 on my Macbook 1,1 and I say myself that is a good idea try to share the basics things to do to have plain support.
I'm new to wiki so I need some reference to learn how to set a page... so if anyone can help me or suggest me a good page as "template" for a macbook1,1/Jaunty page will be very appreciated! :D
(and also who will do a strong review of my english! :( )

---

### Post by cyberdork33 on 2009-02-18
> **mirkop said:**
> Hi all!
I'm a quite long time Ubuntu user (for work, study and "fun" stuff) and I've found always the right answer in MactelSupport pages ;)
Now I'm running with success (K)Ubuntu 9.04 on my Macbook 1,1 and I say myself that is a good idea try to share the basics things to do to have plain support.
I'm new to wiki so I need some reference to learn how to set a page... so if anyone can help me or suggest me a good page as "template" for a macbook1,1/Jaunty page will be very appreciated! :D
(and also who will do a strong review of my english! :( )
[https://wiki.ubuntu.com/MactelSupportTeam#How%20to%20create%20a%20Mactel%20wiki](https://wiki.ubuntu.com/MactelSupportTeam#How%20to%20create%20a%20Mactel%20wiki)

There are several links, and information on getting started. There is also a link to a template. You can just copy and paste the source from the template page into your new wiki page.

Thanks for getting this started!

---

### Post by inphektion on 2009-03-05
Currently on this page: [https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam)
I've added the MacBookPro 5,2 so that I could link to the 5,2 Jaunty wiki created.  However looking at the format it would probably be better served making it 5-1_5-2 as others followed that format.  But there is a ripple effect as I'd have to rename the wiki I started from 
[https://help.ubuntu.com/community/MacBookPro5-2/Jaunty](https://help.ubuntu.com/community/MacBookPro5-2/Jaunty)
to
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty)
which I don't know how to do.

Then this page [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) which lists a MacBookPro 5,1 should technically say MacBookPro 5,1 & 5,2 as the others do.  And then to make sense instead of linking here: [https://help.ubuntu.com/community/MacBookPro5-1](https://help.ubuntu.com/community/MacBookPro5-1)
it should link to [https://help.ubuntu.com/community/MacBookPro5-1_5-2](https://help.ubuntu.com/community/MacBookPro5-1_5-2).

and then on that page we can add the link to the jaunty wiki which would be [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty).

So anyone know how to best accomplish this?

---

### Post by cyberdork33 on 2009-03-05
> **inphektion said:**
> Currently on this page: [https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam)
I've added the MacBookPro 5,2 so that I could link to the 5,2 Jaunty wiki created.  However looking at the format it would probably be better served making it 5-1_5-2 as others followed that format.  But there is a ripple effect as I'd have to rename the wiki I started from 
[https://help.ubuntu.com/community/MacBookPro5-2/Jaunty](https://help.ubuntu.com/community/MacBookPro5-2/Jaunty)
to
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty)
which I don't know how to do.
Don't rename it, you copy it, and then put a redirect statement in the old page to redirect to the new page. like this:
```
#redirect MacBookPro5-1_5-2/Jaunty
```> **inphektion said:**
> Then this page [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) which lists a MacBookPro 5,1 should technically say MacBookPro 5,1 & 5,2 as the others do.  And then to make sense instead of linking here: [https://help.ubuntu.com/community/MacBookPro5-1](https://help.ubuntu.com/community/MacBookPro5-1)
it should link to [https://help.ubuntu.com/community/MacBookPro5-1_5-2](https://help.ubuntu.com/community/MacBookPro5-1_5-2).

and then on that page we can add the link to the jaunty wiki which would be [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty).

So anyone know how to best accomplish this?
You can make those edits. though the redirect will fix the links.

---

### Post by inphektion on 2009-03-05
ok made some changes. pls someone else check them over i tried not to make any blundering mistakes.

---

### Post by cyberdork33 on 2009-03-06
> **inphektion said:**
> ok made some changes. pls someone else check them over i tried not to make any blundering mistakes.
i get an email everytime you update one of the pages. Nothing jumped out at me as looking bad. I checked out your page. Looks good.

---

### Post by inphektion on 2009-03-06
> **cyberdork33 said:**
> i get an email everytime you update one of the pages.
haha, sorry about that then.  later on I realized there was a preview button....

---

### Post by cyberdork33 on 2009-03-08
> **inphektion said:**
> haha, sorry about that then.  later on I realized there was a preview button....
it's my choice. I subscribe to several wikis.

---

### Post by Bad Penguin on 2009-09-02
I have recently experienced a big fat FAIL when attempting to upgrade my MBP5,4 to snow leopard after having had followed the wiki instructions to get jaunty installed.  The particular problem I ran into is documented in this [apple discussion topic](http://discussions.apple.com/thread.jspa?threadID=2130966&start=90&tstart=300).

I have done absolutely no research on this yet, but I believe my problem might have been a result of allowing the ubuntu installer to use all free space on the disk for installation.  I noticed after using boot camp to initially split the disk, it leaves 128M free space between the partitions.

I was just wondering if anyone else here has experienced the same issue, and if so, perhaps the wiki needs to be updated to show users how to manually create the partitions, leaving 128M free space between any apple partition and the partitions created for installing ubuntu.

Just food for thought.

---

### Post by Bad Penguin on 2009-09-06
> **Bad Penguin said:**
> The particular problem I ran into is documented in this [apple discussion topic](http://discussions.apple.com/thread.jspa?threadID=2130966&start=90&tstart=300).


Just a follow up, a couple of people have posted to the apple discussion thread linked above with a confirmation of the problem and solution...

---

### Post by beauman on 2009-11-14
Hi!

I created 

[https://help.ubuntu.com/community/MacBook4-1/Karmic]("https://help.ubuntu.com/community/MacBook4-1/Karmic").

Since a lot in v9.10 has improved, it turns out to be much smaller compared to the [wiki for v8.10]("https://help.ubuntu.com/community/MacBook4-1/Intrepid").

Some things still have to be tested & documented:
[LIST]
[*]swapping <,> with ^,°
[*]firewire
[*]external monitor with and without compiz
[*]apple remote 
[*]the section "Accessing media keys with the fn-key" is untested, because I prefer the default layout
[/LIST]

I had problems swapping the keys for <,> with ^,°. The entry "Swap keycodes of two keys when Mac keyboards are misdetected by kernel" is missing in 9.10. But maybe I should start a new thread to solve this particular problem.

I can check the external monitor some day, but I don't have an apple remote. I could test firewire with my external sound card, but I have never tried that with Linux before. So, it would be great, if somebody could test it and complete the wiki!


The 9.10 release is also solving a big problem for me: My USB-UMTS modem made my kernel freeze after a while
being online. This is fixed now! (It will only freeze, if I am online und unplug the modem)  :p

Greetings to the Mactel social group!
Beauman

---

### Post by buntuLo on 2009-11-14
> **beauman said:**
> I had problems swapping the keys for <,> with ^,°. The entry "Swap keycodes of two keys when Mac keyboards are misdetected by kernel" is missing in 9.10. But maybe I should start a new thread to solve this particular problem.
indeed, that option has been taken out. you can use xmodmap as explained here, just use the keys that are on your keyboard, as i have different ones.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214786]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214786")

---

### Post by beauman on 2009-11-16
:KS  The [wiki for installing Karmic on the Macbook 4th generation]("https://help.ubuntu.com/community/MacBook4-1/Karmic") is done! :KS  :popcorn:


Well, almost. Only the section on how to install the remote is missing. 

Maybe someone with an apple remote and a MB4.1 would like to volunteer to check it out and complete the wiki? 

(In best case it will be equal to the section from MB2.1 and you can copy & paste it)

Thanks in advance,
beauman

---

### Post by Nikos.Alexandris on 2009-11-16
> **beauman said:**
> :KS  The [wiki for installing Karmic on the Macbook 4th generation]("https://help.ubuntu.com/community/MacBook4-1/Karmic") is done! :KS  :popcorn:

Sorry guys but shouldn't it read **Ubuntu 9.10 on MacBook** and *not* **MacBook (4,1) on Ubuntu 9.10 (Karmic Koala)** as it is currently?

Regards

---

### Post by Nikos.Alexandris on 2009-11-17
> **Nikos.Alexandris said:**
> Sorry guys but shouldn't it read **Ubuntu 9.10 on MacBook** and *not* **MacBook (4,1) on Ubuntu 9.10 (Karmic Koala)** as it is currently?

Regards

The same here [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic) and perhaps in more pages.

---

### Post by beauman on 2009-11-17
You tried to set up the Apple remote on a MBP5.1 and you didn't make it work? Well, that is at least a start. In this case you should open a new thread. 

We shouldn't copy an installation guide from one wiki to the next. Not if the guide was not tested at least once on the second hardware. 

Good luck!

---

### Post by beauman on 2009-11-17
> **Nikos.Alexandris said:**
> Sorry guys but shouldn't it read **Ubuntu 9.10 on MacBook** and *not* **MacBook (4,1) on Ubuntu 9.10 (Karmic Koala)** as it is currently?

Regards :lol: Not a bad one. 

You have to admit, in the end it was worse all the time we spend discussing.

---

### Post by Nikos.Alexandris on 2009-11-17
> **beauman said:**
> You tried to set up the Apple remote on a MBP5.1 and you didn't make it work? Well, that is at least a start. In this case you should open a new thread. 

We shouldn't copy an installation guide from one wiki to the next. Not if the guide was not tested at least once on the second hardware. 

Good luck!

Hi Beauman. To whom are you directing your question (You tried... )? I did try and did not succeed. And I added a Note. 

I see that there are several stuff in the wiki which are just copy from older versions. Yes, we should be more careful with those. Nevertheless, I never copy-paste things that I don't test. + if I do, I do mention that something is untested.

Regards

---

### Post by beauman on 2009-11-18
> **Nikos.Alexandris said:**
> The same here [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic) and perhaps in more pages.

I referred to this comment. But it was a misunderstanding. Sorry!

---

### Post by zethes on 2009-11-25
Hola Amigos
Hi there so a newbie here but i get the feeling im going to like being here. So i have a macbook 2,1. i already add to the hardware in the group, but i'm not sure if i was suppoded to do it or someone else. Any way im going to start with a set of pictures of me installing ubuntu 9.10 to my macbook so we can use them in the apple install. Be free to contact me and show me my mistakes. by the way my native lenguage is spanish. sorry for the spealling.

---

### Post by beauman on 2009-11-26
Yes, contribute to the user documentation! The picture in [help.ubuntu.com/community/MacBook2-1/Karmic]("https://help.ubuntu.com/community/MacBook2-1/Karmic") seems indeed to be broken. 

> **zethes said:**
>  sorry for the spealling.

Never mind ! [IMG]http://1.2.3.9/bmi/www.ubuntu-austria.at/images/smiles/icon_lol.gif[/IMG] If the language of your browser is spain, you might consider to install a second browser with english language support. You can than use the spell checker.

So, welcome!

---

### Post by Appleshare on 2009-12-07
Hi All,

I'm a new support team member. First of all I'd like to thank you all for the great work that made installing and configuring Ubuntu on my new MacBook Pro 5,4 maybe not a breeze, but certainly much, much easier than it would have been.

I'd like to contribute, have started to acquaint myself with the support team wiki pages, and started to read this discussion thread (which will take quite some more time). That is, as far as time is left aside from playing with this really neat laptop. In the process of installing and configuring I have started to add to the pre-existing 5,4-specific stuff on the [https://help.ubuntu.com/community/MacBookPro5-5/Karmic](https://help.ubuntu.com/community/MacBookPro5-5/Karmic) page, which consequently has become a bit messy. I thought about making a separate page for the 5,4 but that would double maintenance work, and with the release of pommed 1.31 the current special-casing of pommed 1.30 for the 5,4 should go away again. Let me know what you prefer, though.

I have also just added a new table for Karmic (was still missing) on the MactelSupportTeam page, [https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam), and added myself. I also added the mbp 5,4 to the "hardware currently in team" list.

In the nearer future my main interest will probably be to finally make the Apple remote work, to look more into power saving measures that can reasonably be applied to the mbp, and remaining issues I have with the touchpad. More about these later in other posts, I guess.

And one more thing: I am thinking about having stickers printed with the Ubuntu Mactel logo. Would this be ok by everyone, or could someone point me to the license (which I could not find)? The stickers would be made such that they can be put on the glowing Apple lid logo, i.e., matching size, transparent, UV-resistant. My limited research so far found no online print service that offers such stickers in amounts lower than 50. Which means I could send out some to you guys - send me an email if you are interested.

Cheers
Mario

---

### Post by cyberdork33 on 2009-12-08
Hello!

There are some guides on getting the remote working around. I do not know if they support the newer remotes that just cam e out recently though.

I obtained the logo image from another user (former maybe) of the ubuntu forums. I inquired about the use of the image and was given full rights to do whatever we like with it. See inquiry below:

[quote=thecommodore]Hey! Yeah, I am not a forum person :D:D It takes a lot of time and dedication and I am quite busy with school and life.

About the logo, here is the .svg [http://www.wolvenstudios.com/z_The%20Common/Pictures/appleubuntu.svg](http://www.wolvenstudios.com/z_The%20Common/Pictures/appleubuntu.svg) -- just make sure you download it cause I'll remove it eventually...

Feel free to use it, modify it, change it, whatever you want, and I don't care about the credit. Call it your own if you like.

Best,

Luke Holmes (***Email Removed - CD33***)

[quote=cyberdork33]I know that you haven't been in the forums for awhile, but there is a large group of Intel Mac users running Ubuntu that are forming a team in launchpad. I would like to use your Ubuntu-Apple logo as part of our artwork, possibly even the team logo. 

Thanks[/quote][/quote]

The link no longer works, but I have the svg somewhere. Let me know if you need it (PM).

---

### Post by Canavas on 2009-12-13
Hi!
 
[SIZE=2]1st of all many thanks to this documentation:[/SIZE]
 
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic)
 
[SIZE=2]With my **Macbook pro 5,2 and Ubuntu 9.10** i had no sound too,[/SIZE]
[SIZE=2]but i found a solution.[/SIZE]
 
[SIZE=2]First of all the line "**aptitude install linux-backports-modules-alsa-karmic" **in the documentation is wrong.[/SIZE]
 
[COLOR=black][FONT=Times New Roman][COLOR=black][FONT=Times New Roman]*[FONT=Verdana][SIZE=2]**linux-backports-modules-alsa-karmic-generic**[/SIZE][/FONT]*[/FONT][/COLOR][/FONT][/COLOR]
[SIZE=2]is the right one.[/SIZE]
 
[SIZE=2]After this you have to find the right soundprocessor.[/SIZE]
[SIZE=2]I did this with alsamixer, you see the soundcard and procesor on the top left.[/SIZE]
[SIZE=2]Mine is a ALC889A.[/SIZE]
 
[SIZE=2]Then take a look at this list...[/SIZE]
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt#126](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt#126)
 
[SIZE=2]ALC889 seems good to me so i added ***options snd_hda_intel model=mb5** *in the [FONT=Times New Roman]*[FONT=Verdana]**/etc/modprobe.d/options.conf.**[/FONT]*[/FONT][/SIZE]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=2]Reboot -> and checked all the sliders in the Audio-properties because one was muted.[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=2]After this sound worked fine.[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=2]Hope it helps and the author is reading my post,[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Verdana][SIZE=2]so he is able to change his documentation.[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=2]regards,[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Verdana][SIZE=2]Canavas.[/SIZE][/FONT][/FONT]

---

### Post by Appleshare on 2010-02-05
Hi all, I've been quite quiet after my noisy welcome, sorry for that, lot's of private stuff suddenly interfered. I just wanted to let you know that I have installed Lucid on my MacBook Pro 5,4 and that it works mostly fine. Documentation is at [https://help.ubuntu.com/community/MacBookPro5-4/Lucid](https://help.ubuntu.com/community/MacBookPro5-4/Lucid) so please add stuff if you know more, correct my mistakes, and give general feedback - I guess some of it should better be on pages that apply to all Mactels, not the hardware-specific page.

Cheers
Appleshare

---

### Post by Appleshare on 2010-02-05
> **Canavas said:**
> Hi!
 
[FONT=Times New Roman][FONT=Verdana][SIZE=2]Hope it helps and the author is reading my post,[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Verdana][SIZE=2]so he is able to change his documentation.[/SIZE][/FONT][/FONT]
 
[FONT=Times New Roman][FONT=Verdana][SIZE=2][/SIZE][/FONT][/FONT]

Thanks for posting the information. Just so you know, you can make this change on the help page yourself if you want to. If you do, add a comment about the reasons for the change when saving, to help the main editor (if any) understand.

---

### Post by linuxopjemac on 2010-02-05
sorry, can someone delete this post pls ?

---

### Post by Appleshare on 2010-02-22
Does anybody know what's up with the page [https://help.ubuntu.com/community/MacBookPro5-5/Lucid](https://help.ubuntu.com/community/MacBookPro5-5/Lucid) ?
It apparently was created yesterday by copying [https://help.ubuntu.com/community/MacBookPro5-5/Karmic](https://help.ubuntu.com/community/MacBookPro5-5/Karmic) and it was linked from the main page [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

But scarcely anything else was done, so now we have a page that pretends to be for Lucid, but simply contains the Karmic content. The guy who changed it has no email address listed. I just removed the reference to the MBP 5,4 from the headline because I've created a (much better) page for 5,4 quite a while ago, [https://help.ubuntu.com/community/MacBookPro5-4/Lucid](https://help.ubuntu.com/community/MacBookPro5-4/Lucid)
It would have been better if this had been copied for the MBP 5,5. Or even better still, a 5,5 owner should have checked if there are any differences at all that warrant a separate 5,5 page.

So what now? What's the recommended procedure in this case?

---

### Post by abel_bcn on 2010-04-18
Hey there.

Is there any planning on benchmarking ubuntu with the latest released Macbook Pro's, as of April 2010? Would everything still be the same as for the 2009 ones regarding installation and configuration?

I've been a while waiting for apple to finally release them and just ordered one, but of course, won't be able to live without ubuntu installed. So, what's the deal?

Thanks!

---

### Post by kosumi68 on 2010-04-18
> **abel_bcn said:**
> Hey there.

Is there any planning on benchmarking ubuntu with the latest released Macbook Pro's, as of April 2010? Would everything still be the same as for the 2009 ones regarding installation and configuration?

I've been a while waiting for apple to finally release them and just ordered one, but of course, won't be able to live without ubuntu installed. So, what's the deal?

Thanks!

As you say, brand new, and most likely brand-new problems :-) Just start a thread when you have had a chance to test it a bit, and this wonderful community will help out, I'm sure.

---

### Post by abel_bcn on 2010-04-19
> **kosumi68 said:**
> As you say, brand new, and most likely brand-new problems :-) Just start a thread when you have had a chance to test it a bit, and this wonderful community will help out, I'm sure.

Great thanks I was just making sure I wasn't missing anything.

Cheers!

---

### Post by bfroemel on 2010-05-04
Hello everyone,

I recently joined you to get Ubuntu fully up and running on my  MacBookPro6,2 . Just to let you  know, I started a wiki page 

[https://help.ubuntu.com/community/MacBookPro6-2/Lucid](https://help.ubuntu.com/community/MacBookPro6-2/Lucid)

and linked it from

[https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

It's still a work in progress (a lot of things - most importantly pommed (depends on brightness), brightness, wireless and front speakers - aren't working (properly)) - but I hope I(/we) can fix that soon.

See you,
  bf

---

### Post by rmdegennaro on 2010-05-04
Hello everyone,

I just installed 10.04 Lucid on my Macbook Pro 3,1.  Two reasons to ask a question on the forums:
[LIST=1]
[*]The page [https://help.ubuntu.com/community/MacBookPro3-1](https://help.ubuntu.com/community/MacBookPro3-1) shows " (Lucid Lynx) - Beta1".  Is it protocol for me to remove " - Beta1"
[*]Also, for sound I had to add the same options as with Karmic.  Should I just add that to this page: [https://help.ubuntu.com/community/MacBookPro3-1/Lucid](https://help.ubuntu.com/community/MacBookPro3-1/Lucid) ?
[/LIST]

Sorry if the questions seem silly.  I've not done much with community documentation.

Best,
Rio

---

### Post by kosumi68 on 2010-05-05
> **bfroemel said:**
> Hello everyone,

I recently joined you to get Ubuntu fully up and running on my  MacBookPro6,2 . Just to let you  know, I started a wiki page 

[https://help.ubuntu.com/community/MacBookPro6-2/Lucid](https://help.ubuntu.com/community/MacBookPro6-2/Lucid)

and linked it from

[https://wiki.ubuntu.com/MactelSupportTeam](https://wiki.ubuntu.com/MactelSupportTeam)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

It's still a work in progress (a lot of things - most importantly pommed (depends on brightness), brightness, wireless and front speakers - aren't working (properly)) - but I hope I(/we) can fix that soon.

See you,
  bf

Welcome!

---

### Post by Chesamo on 2010-12-25
[https://help.ubuntu.com/community/Mac_mini3-1/Maverick](https://help.ubuntu.com/community/Mac_mini3-1/Maverick)

Linked on [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by patientfox on 2011-03-01
Hi,
I've started stubbing out a doc page for the 8,1 MBP on Natty. It is linked on the main Mactel wiki page and is located at: [https://help.ubuntu.com/community/MacBookPro8-1/Natty](https://help.ubuntu.com/community/MacBookPro8-1/Natty)

Pretty much all that's been done, so far, is stubbing over the overview/status icon from the 7,1 Maverick page and linking to a thread in the Apple Users forum where some people with 8,1 MBPs are working through initial setup issues. I personally haven't picked up my 8,1 yet (probably this weekend), just want to provide a place for anyone who can contribute to be able to do so.

Thanks

---

### Post by moogman on 2011-04-02
Suggestion for supported versions.

Hi, I'd like to make a suggestion for [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Mactel%20Wiki%20Support%20Matrix](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Mactel%20Wiki%20Support%20Matrix) and it's sub-pages...

There's far too much choice.  For every hardware model, I think we should have a maximum of three different choices:

* The most recent Ubuntu LTS release
* The most recent Ubuntu release
* The best supported (hopefully this is either the LTS, or the most recent version!)

I don't think we should be encouraging users to install Ubuntu 8.04, unless it provides a far better user experience than 10.04/10.10 (or soon, 11.04).

Thoughts?

---

### Post by itismike on 2011-04-02
> **moogman said:**
> I think we should have a maximum of three different choices:

* The most recent Ubuntu LTS release
* The most recent Ubuntu release
* The best supported (hopefully this is either the LTS, or the most recent version!)


Great idea.

---

### Post by itismike on 2011-04-02
Maybe we can archive links to the older pages somewhere. Does anyone know of an easier way to edit the matrix? Going through the code by hand and taking out the ||'s is tedious!

---

### Post by moogman on 2011-04-03
> **itismike said:**
> Maybe we can archive links to the older pages somewhere.

The product wiki pages still contain the entire list of pages, perhaps that's a suitable archive?


> **itismike said:**
> Does anyone know of an easier way to edit the matrix? Going through the code by hand and taking out the ||'s is tedious!


Unfortunately, the ubuntu wiki doesn't have the GUI editor (otherwise it'd be [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages?action=edit&editor=gui](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages?action=edit&editor=gui))

So I exported it to moinmo.in, and edited with it's gui instead ([http://moinmo.in/4ct10n/edit/WikiSandBox2?action=edit&editor=gui](http://moinmo.in/4ct10n/edit/WikiSandBox2?action=edit&editor=gui)).  A little nasty, but hopefully it's a one-off, and now the versions won't change often.


I've added the new simpler table, but left the old table there - take a look and see what y'all think: [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by itismike on 2011-04-03
> **moogman said:**
> The product wiki pages still contain the entire list of pages, perhaps that's a suitable archive?

What product pages?
[edit - neverind. I found them.]

> **moogman said:**
> take a look and see what y'all think: [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

Fantastic! Really nice work, Moogman!

But now that I see the layout, I don't like a separate column for "Best supported release." 
Instead it can be indicated by a footnote, **highlight**, asterisk *, or other easily-identified mark :KS within the normal columns of:
Most recent release || LTS || Testing

Or do we just need two columns:
Most recent release || LTS

On that topic: Who's to decide what the "Best supported release" is? Ideally, an algorithm could decide this based on the number of check-marks ([IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=check_small.png[/IMG], [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=check_remark_small.png[/IMG], [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=warning_small.png[/IMG], [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=dont_small.png[/IMG], [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=query_small.png[/IMG]) a support page has earned, with a weight added for importance (fan & sensors = 10, Apple remote control = 2, etc.)

Realistically, those that maintain these pages will arbitrarily decide which version is 'best supported' based on their own experience and duke it out on this forum. In this case, I'd like to demote Natty Narwhal to the 'Most recent release' or 'testing' column as there are still significant open bugs with Natty.

---

### Post by siepo on 2011-04-03
The referenced page suggests that newer versions do not work. Maybe you should replace 'Most recent release' with 'Most recent confirmed release'. 
E.g. my Macbook has been updated from release to release, from Dapper Drake to Maverick Meerkat, and works absolutely fine, but I have no idea anymore of what a fresh install nowadays would entail.
So unfortunately I am not in a position to contribute to the matrix.

---

### Post by moogman on 2011-04-04
> **itismike said:**
> 

But now that I see the layout, I don't like a separate column for "Best supported release." 
Instead it can be indicated by a footnote, **highlight**, asterisk *, or other easily-identified mark :KS within the normal columns of:
Most recent release || LTS || Testing

Or do we just need two columns:
Most recent release || LTS


What happens when the best supported release isn't the most recent, nor the LTS (or the testing)?



> **itismike said:**
> 
On that topic: Who's to decide what the "Best supported release" is? Ideally, an algorithm could decide this based on the number of check-marks ([IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=check_small.png[/IMG], [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=check_remark_small.png[/IMG], [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=warning_small.png[/IMG], [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=dont_small.png[/IMG], [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=query_small.png[/IMG]) a support page has earned, with a weight added for importance (fan & sensors = 10, Apple remote control = 2, etc.)

Realistically, those that maintain these pages will arbitrarily decide which version is 'best supported' based on their own experience and duke it out on this forum. In this case, I'd like to demote Natty Narwhal to the 'Most recent release' or 'testing' column as there are still significant open bugs with Natty.


I think it's sane to judge by the amount of ticks in the respective pages :-)

And people are watching the wiki page, so I'm sure the 'best supported' version will bounce between a number of versions, before settling on something that everyone agrees on.

---

### Post by moogman on 2011-04-04
> **siepo said:**
> The referenced page suggests that newer versions do not work. Maybe you should replace 'Most recent release' with 'Most recent confirmed release'. 
E.g. my Macbook has been updated from release to release, from Dapper Drake to Maverick Meerkat, and works absolutely fine, but I have no idea anymore of what a fresh install nowadays would entail.
So unfortunately I am not in a position to contribute to the matrix.


That's a fair criticism.  I'm Not sure about the wording 'confirmed' though, as it may be read as 'fully supported' - which may not be true.  How about 'most recently tested release', 'most recently tested LTS'?


My real goal was to reduce the amount of options, irrelevant to the majority of people - I don't want someone downloading Ubuntu 8.04 if 10.10 or 10.04 is better supported.  Equally if 8.04 is best supported, then I think it's right to encourage them to use that instead of 10.10, regardless of whether it's officially supported by Ubuntu or not.

---

