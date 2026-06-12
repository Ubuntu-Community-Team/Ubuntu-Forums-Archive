---
title: "Why doesn't Ubuntu offer the option of a separate /home partition on install?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by ramjet_1953 on 2007-04-12
I have often wondered why Ubuntu doesn't offer the simple option of creating a separate /home partion, when doing a fresh install?

As far as I know, having a separate /home partition is good practice.

I know it can be done manually in parted, but for those of us trying to escape from Wndows and not used to such things, manually partitioning can be terrifying, especially if a new user wants to keep his Windows partition, as a security blanket.

The how-to in psycocats is easy enough for those of us used to the command line, but for a newbie, it would have him running for cover.

Surely, a question asking if you would like a separate partition for /home and its' benefits would be an easy addition to the installer script?

Just a thought.

Any comments, criticisms?

Regards,
Roger :cool:

---

### Post by freebird54 on 2007-04-12
I think that the devs fear that having a separate swap partition is already approaching overload for a n00b.  Would be nice as an extra option though - leaving maybe 7 Gb for the root / .

Having spent years trying to get Windows to stop putting everything on C drive, I went immediately to manual mode - but not everyone has that kind of mindset!

---

### Post by raul_ on 2007-04-12
What's the problem? Create a new partition and mount /home there, as you do witth / and swap... I don't really feel there is a need for an option. And if you want, you can just move all your home data to another partition. Is not a nightmare. Basically is just copying everything to another partition and editing fstab.

Although, IMHO, one could replace the (rather idiotic) obligation to have a swap partition, for this option

---

### Post by justleen on 2007-04-12
IMHO, if your not familiar enough with manual part. edits, you have no need for a seperate /home ..

---

### Post by ramjet_1953 on 2007-04-12
Raul and Justleen, I think you both have totally missed the point of my post.

I'm talking about people who are trying to migrate from Windows to Linux and have virtually no experiece with the command line.

I'm sure that both of you know that it is just good housekeeping practice to have a seperate partition for your /home directory.

The suggestions made by raul are fine to an experieced user, but to a new user of Linux, what you are suggesting is way outside of their comfort zone.

As I originally stated, whay can't the developers just add a simple Yes/No question in the install script, for the addition of a /home partition?

Not exactly rocket science, is it?

Regards,
Roger :cool:

---

### Post by zvacet on 2007-04-13
O.K. Just imagine that kind of situation,someone without any previous knowledge of linux is installing,and comes to question &#733;Do you want separate home partition?¨It is confusing question,because that man doesn´t know what home partition is,how much space to give to it...
Another reason could be that you have small partition and you don´t have space for home.In that case you are still able to install linux,but with root and swap only.If you have enough space for home partition and you didn´made it with expirience in linux you will be able to make it later.

---

### Post by hyper_ch on 2007-04-13
I think the problem is all kinds of people are installing Linux on all kinds of hardware... how would you split up a 7GB harddisk? How would you split up a 500GB harddisk?

With two partitions (root and swap) you have a complicated design already to decide for... by adding a third one it will be a complex scheming of that drive...

People who come first time on linux will be more than happy to have /home on the root... if they decide to make it seperate it's also quite simple to achieve :) so I don't really see a reason why making the install more complex on that issue.

---

### Post by justleen on 2007-04-13
I think i do understand your question, actually.
For me personally, i agree with you. But there are loads of people trying Ubuntu at this stage, and i dont think it will be a clear advantage for those new users.

If somebody moved from windows, with no experience in linux at all, then in my opinion, they have no need for a seperate home drive.. Why would they need it?
Yes, i have one, for practical reason of sharing my home dir on different installs. Buts really, thats about it, isnt it? For backup purposes it doenst matter - i wouldnt backup TO my home dir.. i have seperate drive for that too.

I can imagine the scenario of a starter having to reinstall, and thus losing is /home folder.. but i really wonder what kind of data you'd have there that is critical at that stage

If one becomes familiar/advanced enough that he thinks "hey, a seperate /home partition would be reaaaally nifty..."  i recon he will be at a stage that he can manually edit the partition during install (or afterwards).

in comparison: on my windows machine, My Docs is located on a different partition as well. I have to change that by hand.. I wouldnt want to explain my Dad (just a random example of a silly user) why windows is asking where his My Docs should be located during install, really..
(yes, he WOULD be rining me for an answer to that :) )

so, in the end i  think adding a simply yes/no question for a seperate /home will end up in more simple questions on this forum..

---

### Post by Fascination on 2007-04-13
> **ramjet_1953 said:**
> I'm sure that both of you know that it is just good housekeeping practice to have a seperate partition for your /home directory.

Theres lots of 'good housekeeping practice' methods that I think should be used, but as mentioned your average user just starting out in Linux doesnt care. :)
I think the 'newbie' installation method offered by Ubuntu at the moment is great for a new start, and its then down to the user to learn more about partitions as he or she gains more knowledge and re-partition to the way they feel is most appropriate. :)

---

### Post by GSF1200S on 2007-04-13
> **justleen said:**
> I think i do understand your question, actually.
For me personally, i agree with you. But there are loads of people trying Ubuntu at this stage, and i dont think it will be a clear advantage for those new users.

If somebody moved from windows, with no experience in linux at all, then in my opinion, they have no need for a seperate home drive.. Why would they need it?
Yes, i have one, for practical reason of sharing my home dir on different installs. Buts really, thats about it, isnt it? For backup purposes it doenst matter - i wouldnt backup TO my home dir.. i have seperate drive for that too.

I can imagine the scenario of a starter having to reinstall, and thus losing is /home folder.. but i really wonder what kind of data you'd have there that is critical at that stage

If one becomes familiar/advanced enough that he thinks "hey, a seperate /home partition would be reaaaally nifty..."  i recon he will be at a stage that he can manually edit the partition during install (or afterwards).

in comparison: on my windows machine, My Docs is located on a different partition as well. I have to change that by hand.. I wouldnt want to explain my Dad (just a random example of a silly user) why windows is asking where his My Docs should be located during install, really..
(yes, he WOULD be rining me for an answer to that :) )

so, in the end i  think adding a simply yes/no question for a seperate /home will end up in more simple questions on this forum..

I agree here.

Ultimately, I think it depends on the user. 

When I really got serious about Linux, I researched it for DAYS.. I looked at all the different distributions, the pros and cons, the difference between debian and rpm based distros, potential problems with the partitioning, where the bootloader should be, etc, etc... I knew my noobness and I attacked it to try and be as well informed as I could be. But, im pretty good with computers, and I knew how complicated things could get.

For the average windows user who has no clue about the innerds of a computer, or how everything is setup, this /home partition is going to be even more stifling.. I found myself pausing a few times to make sure I was on the right path.. I think that a person should have the easiest install process possible. Let them get into the OS and figure out its gears.

Then, and only then, they can start branching out into what they need to have backed up, and how they want the OS to respond to there inputs. As a final note, unless were talking about multiple Linux distros, there isnt going to be too much of a purpose. NTFS3g can read/write to the windows partition. All I do is save my important stuff in "My Documents." Linux can always read it, and if Linux crashes, then Windows can read it. Besides, when does Linux crash? As an expierienced windows user, Ive had windows crash. As a complete Noob, Ubuntu hasnt crashed ONCE!

---

### Post by louieb on 2007-04-13
Two things come to mind. Keep it simple (Kiss) the more options a person has the more ways there are to screw it up.  The person new to installing a operating system does not need another option. I've seen the posts where some have messed up their windows partition using the slider bar.  or just saw one where the guy turned his 100+ gig windows partition into a swap partition, then wondered where windows went.:confused:

The other thing is if a person is Linux savvy enough to  know that a partition for /home is a good thing. Then they can figure out how to use manual partitioning. But like someone said I would not want to explain that to  my wife. :D

---

### Post by grimpage on 2007-04-13
Another quick question, during my first xubuntu install, having already set up my desired partitions will the installation process format all my data? I get this warning:

[I][strong]WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.[/I][/strong]

Does this mean that even partitions that I remove from the prior menu will be formatted, or will this only happen to the selected information on the partitions I have included? 

I guess what I'm asking is do I need to do a fresh install, or can xubuntu be added safely over pre-existing data?

---

### Post by InuyashaDuelist on 2007-04-13
> **zvacet said:**
> O.K. Just imagine that kind of situation,someone without any previous knowledge of linux is installing,and comes to question &#733;Do you want separate home partition?¨It is confusing question,because that man doesn´t know what home partition is,how much space to give to it...
If they don't understand, tell them it's the equivalent of the Documents and Settings folder on Windows.

---

### Post by Bushfire on 2007-04-13
> **InuyashaDuelist said:**
> If they don't understand, tell them it's the equivalent of the Documents and Settings folder on Windows.
Yeah, and the Windows installer doesn't give the option, and everyone praises it for user friendliness.

I agree with everyone else here, once somebody has enough knowledge to know why a seperate /home partition is a good thing, they can do it by hand. It would only make the installer _more_ complicated.

---

### Post by ComplexNumber on 2007-04-13
> **Bushfire said:**
> Yeah, and the Windows installer doesn't give the option, and everyone praises it for user friendliness.

I agree with everyone else here, once somebody has enough knowledge to know why a seperate /home partition is a good thing, they can do it by hand. It would only make the installer _more_ complicated.
well, i agree. whilst  the OP is referring to those coming from windows, i believe that those doing so already have enough common sense to know to expect something different and to not expect Windows Version 2. its the same as when anyone migrates from windows to mac, mac to linux, linux to windows, or whatever.

the OP, in a way, gives me the impression that windows is the epitome of userfriendliness. obviously, it isn't,  yet windows does not take into account those people that are used to macs or linux or those that have never used a computer before. for example, windows offers no way to easily and intuitively have a separate partition for one's settings and documents - that is a negative point for windows. also, windows only takes into account past windows users.  if, for example, i migrated from linux to windows vista(which i haven't tried yet), many of the aspects of windows that are unfamiliar will appear to be alien to me and un-userfriendly. thats not to say that that automatically makes them un-userfriendly. for example, if MS wants more market share(and it clearly does), why doesn't windows clearly state during the install process that there is no facility to have a home user directory? if i were ignorant, i would say that that is downright un-userfriendly.

many people (wrongly) equate unfamiliarity with un-userfriendliness.

---

### Post by kelvin spratt on 2007-04-13
I,m A new Linux User and i'm no idiot so why is everybody asuming that myself and all new users are idiots you were asked a simple question so why not answer a simple question not try to make out that we are idiots or of low iq if i'd known about a home partition i'd have done it straight away
and that would of been that its the i know something you don't that has stopped linux progressing
to more people if these little things were in the open people could decide for them selves and not find out as an after fought:guitar: [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by pppetter on 2007-04-13
> **grimpage said:**
> Another quick question, during my first xubuntu install, having already set up my desired partitions will the installation process format all my data? I get this warning:

[I][strong]WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.[/I][/strong]

Does this mean that even partitions that I remove from the prior menu will be formatted, or will this only happen to the selected information on the partitions I have included? 

I guess what I'm asking is do I need to do a fresh install, or can xubuntu be added safely over pre-existing data?

The installer will format any partition you have selected to be used by Xubuntu. And if you remove partitions, as stated in the warning above, of course the data will be lost. If you already have setup the partition the way you want them to be, then you should of course use the manual partitioning choice (I guess you have already figured that one out).

Next time you have a support question, please go ahead and create a new thread instead of marching in on another one.


> **kelvin spratt said:**
> I,m A new Linux User and i'm no idiot so why is everybody asuming that myself and all new users are idiots you were asked a simple question so why not answer a simple question not try to make out that we are idiots or of low iq if i'd known about a home partition i'd have done it straight away
and that would of been that its the i know something you don't that has stopped linux progressing
to more people if these little things were in the open people could decide for them selves and not find out as an after fought:guitar: [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

Of course you are not an idiot, neither is anyone else. This is rather simple, if you, or anyone else want another setup than the Ubuntu defaults, then feel free to use the Manual partitioning method.

If think that it's wrong to say that the option to put Home in another partition, it IS there!

---

### Post by ComplexNumber on 2007-04-13
> **kelvin spratt said:**
> I,m A new Linux User and i'm no idiot so why is everybody asuming that myself and all new users are idiots you were asked a simple question so why not answer a simple question not try to make out that we are idiots or of low iq if i'd known about a home partition i'd have done it straight away
and that would of been that its the i know something you don't that has stopped linux progressing
to more people if these little things were in the open people could decide for them selves and not find out as an after fought:guitar: [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
take this scenario: what if the situation were that windows has always offered a separate home partition to users during the install but linux has never done so. when you come to linux for the first time, you will be wondering "why is the facility to install a home partition?". you may consider it un-userfriendly that linux doesn't offer that facility because you are used to it with windows. and thats the crux of the matter. its what you are used to.  if that were the case, imagine that you'd never used a computer before, every concept is likely to be alien, and assuming the first time you install windows it gives you the option to have a separate home partition. you'd be thinking "what the heck is this?". on the other hand, if it didn't give you the facility to have a separate home partition, you may be thinking "why doesn't it give me the option to have a separate place to store all my documents so that if i do a reinstall, they are not lost?".

as far as  can see, the option to have a home partition during the linux install is clearly obvious. i'm an idiot and i always found it to be straightforward and logical even in the earliest days. when i first installed linux on my own PC, i knew to expect things to be different and took account of that.

if linux were perfect(in your opinion), how would you like things to be?

btw read my very last sentence in my previous post.

---

### Post by kelvin spratt on 2007-04-13
to move docs and settings in windows is simple right click my doc in menu change where you won't them to go any partition just make a folder and click answer yes to redirect click windows tranfers all your files and associates any progs and files to that folder simplehttp://ubuntuforums.org/images/smilies/guitar.gif

---

### Post by stokedfish on 2007-04-13
Instead of having a seperate /home, I just use RSnapshot to backup it automagically ever night at 3 am!    ;)

---

### Post by ComplexNumber on 2007-04-13
> **stokedfish said:**
> Instead of having a seperate /home, I just use RSnapshot to backup it automagically ever night at 3 am!    ;)
talking about backups, did you know that vista has a backup facility? all versions of vista have the facility to backup one's data, but  if you buy any version lower than premium, you will get  big shock when you come to try to restore it. what microsoft hasn't actually told anyone is that its only possible to recover the backed up data with premium and above. thats not very userfriendly in my book. in fact, its downright deceitful.

---

### Post by hyper_ch on 2007-04-13
> **ComplexNumber said:**
> take this scenario: what if the situation were that windows has always offered a separate home partition to users during the install but linux has never done so. when you come to linux for the first time, you will be wondering "why is the facility to install a home partition?".

How many people do you know who have installed windows themselves and how many do you konw who have never installed an OS themselves?

---

### Post by ComplexNumber on 2007-04-13
> **hyper_ch said:**
> How many people do you know who have installed windows themselves and how many do you konw who have never installed an OS themselves?
 i would struggle to think of anyone who hasn't other than my mum .

---

### Post by kelvin spratt on 2007-04-13
most people i know can install there own os perhaps its because in the uk most people can't afford to get someone else to do do-it for them and as i said before windows does offer a different destination for my documents or any other folder you wanthttp://ubuntuforums.org/images/smilies/guitar.gif

---

### Post by ComplexNumber on 2007-04-13
> **kelvin spratt said:**
> most people i know can install there own os perhaps its because in the uk most people can't afford to get someone else to do do-it for them and as i said before windows does offer a different destination for my documents or any other folder you wanthttp://ubuntuforums.org/images/smilies/guitar.gif
yeah, but during the install process its quite tedious. its not straightforward like it is with linux.

---

### Post by freebird54 on 2007-04-13
My original setup with Windows was rather different.  C: = boot (OS only)  D: = Programs  E: = Data   F: = Games  - others as necessary.  Then came the registry, and suddenly everything HAD to go on C:, and was a TOTAL b___ch to do otherwise.  It is nice that they finally allowed some flexibility in setup again in XP, but that was a LONGGG wait!

Anyway - back to the topic!  I suggest that the simplest answer to the problem is:
A clickable option called* ADVANCED/Manual Partitioning*  - which would discuss the possibilities, before putting you into the manual mode as now.  Reasons for separating /home, andother considerations could be handled with a simple text info file, dumped into a dialog for viewing.  This would be clear to those who either ARE, or consider themselves to be, advanced.  If the subject appears too much for them, let there be a way to back out to the other 2 choices.

This would cover all the objections I think, and people coming from Windows would be used to seeing *'Advanced'* as an option, and ignore or investigate it as matches their preferences.

IMHO - the other 2 options could be made clearer to those who have moderate understanding of computers.  I never considered using them (options 1 or 2) because I didn't KNOW what they would do!  Some way of checking it out would be helpful to that class of 'converters' I think.  Maybe a button with a *'?'* beside all three options would be good - explaining what they actually do?

Beyond that, a MAIN menu entry when the CD boots up,  *'Things to consider before installing'*  might be nice.  A good place to suggest turning off the swap file and triple-running defrag before resizing!

Food for thought?  Food for dogs?  one or the other....  (it is pretty good now)

---

### Post by GSF1200S on 2007-04-13
> **freebird54 said:**
> My original setup with Windows was rather different.  C: = boot (OS only)  D: = Programs  E: = Data   F: = Games  - others as necessary.  Then came the registry, and suddenly everything HAD to go on C:, and was a TOTAL b___ch to do otherwise.  It is nice that they finally allowed some flexibility in setup again in XP, but that was a LONGGG wait!

Anyway - back to the topic!  I suggest that the simplest answer to the problem is:
A clickable option called* ADVANCED/Manual Partitioning*  - which would discuss the possibilities, before putting you into the manual mode as now.  Reasons for separating /home, andother considerations could be handled with a simple text info file, dumped into a dialog for viewing.  This would be clear to those who either ARE, or consider themselves to be, advanced.  If the subject appears too much for them, let there be a way to back out to the other 2 choices.

This would cover all the objections I think, and people coming from Windows would be used to seeing *'Advanced'* as an option, and ignore or investigate it as matches their preferences.

IMHO - the other 2 options could be made clearer to those who have moderate understanding of computers.  I never considered using them (options 1 or 2) because I didn't KNOW what they would do!  Some way of checking it out would be helpful to that class of 'converters' I think.  Maybe a button with a *'?'* beside all three options would be good - explaining what they actually do?

Beyond that, a MAIN menu entry when the CD boots up,  *'Things to consider before installing'*  might be nice.  A good place to suggest turning off the swap file and triple-running defrag before resizing!

Food for thought?  Food for dogs?  one or the other....  (it is pretty good now)

Yeah.. that seems a fair enough solution. People who dont know would be like "F that, Im going to keep it simple" whereas other people who are more informed (I wasnt) will take a look at the text and do it if they feel comfortable...

---

