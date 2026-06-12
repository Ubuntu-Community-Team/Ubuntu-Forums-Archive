---
title: "Shed inventory database - I keep on losing things :("
date: 2018-05-27
forum: Assistive Technology &amp; Accessibility
---

### Post by dmbgo on 2018-05-27
Hi everyone

Over 7 years ago I suffered a serious head on collision with a semi trailer. The associated head injury left me with my memories mostly intact, but I now have a problem remembering things that have happened in the recent past. I think the issue is related to the transfer of memories from my short term memory into my longer term memory.

Prior to the accident I was a systems engineer and my hobbies involved engineering. Over the years I built quite a complex inventory of bits and pieces related to this hobby, including a lathe and a milling machine. All this was housed in my large workshop (40'  x 60'). In the years just after the accident my workshop deteriorated into what would, very kindly, be called a total mess.

I have gone a long way towards solving this problem with the help of my wife however, with the enlistment of a "helper" who comes in twice a week and helps me to organize and tidy things into a usable format.

The new issue that I have found is that although the workshop is tidy and navigable again, I can't find things. Dan (my helper), asks me where I'd like things put, but once he has left, I have forgotten where that location is.

The solution to this new issue, to my mind, is the implementation of a computer based inventory database. This is where having given you some background, I need some help.

The system that I have imagined for the shed would use a database of parts or items and their locations. The system would be easy to use with a GUI that presents the user with a search dialog box. There could be other boxes on the main screen, such as update location or quantities etc.

If the user types 12mm into the search box, they would be presented with everything that has 12mm in the name, things like 12mm bolts, nuts 12mm, 12mm ring spanner etc. If they typed in 12mm spanner into the search box they would get a list of the available 12mm spanners. Selecting one from the list would give them that spanners location.

Locations would be numerical then alphabetical, and where necessary broken into subgroups by number again.

An example of this might be the middle of the 3[SUP]rd[/SUP] shelf on the rack near the roller door. This location could be Rack 1, shelf C section 3, or as it would appear in the search dialog: 1,C,3.

With a virtually illiterate computer user for a helper, and me with a faulty memory, the system has to be robust enough to avoid accidental deletion of data and easy enough to use so that Dan for example, will be able to update the system as he finds homes for things or moves them around.

I haven't been able to find an off the shelf package that meets my needs, but there is probably something out there. Do you have any suggestions? Ideally the system would use a distributed SQL database which could live on my Mythtv backend server, with an OS independent frontend.

I look forward to some help with this, since it would greatly improve, not only my efficiency, but would give me peace of mind knowing that things were no longer lost.

Thanks for your help in advance
Dave

---

### Post by TheFu on 2018-05-27
Would a database really help?  You'd forever be spending time trying to maintain the DB and an incorrect DB is worse than not having one at all.

How may parts/thing types are we talking about here?  My father had a huge tool set, shopsmith, lots of attachments for it and he used large coffee cans with labels on steel shelves to organize things.   "Screws" "Nuts" "Bolts" "Electrical"  All the tools were on a pegboard.  If there was a specific size for anything, it was on the package and he'd leave it inside the packaging, inside the cans.

I use a similar method with my finance/bank/purchases at home.  1 folder per year and large purchases (especially with warranties) are entered into Quicken.  Recipes are put into the folder for 2018 basically in order.  If I need to look up sometime - I'll search quicken for the item - like a "chain saw" - see that I got it in Feb of 1999 for $240.  Clearly out of warranty, but I can find the 1999 folder look near the front (Feb is early in the year) and find it in a few seconds. Sure, I could have partitions for every month, but that would add lots of overhead to the filing system for something I only need to look up 3x a year, at most.  Over complicating things is bad and counter productive.  

If you are amazon with 5M items in the warehouse, then you NEED to keep track of inventory very strictly and ensure the product ASDSDF44445B doesn't get confused with ASDSDF44445D.  People at home probably don't need that strict inventory management.  Simple labels are about the limit. A large photo of the room with "zones" for types of things might be useful to get you close, before looking at the labels.

But only you know the setup and how detailed any grouping needs to be.

---

