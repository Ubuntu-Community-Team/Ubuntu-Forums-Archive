---
title: "Junk Mail in Evolution"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by mediax on 2006-10-12
Does the junk mail filter in Evolution actually do anything? :-k 

I've checked both the "Check incoming mail for junk" and the "Include remote tests" options in preferences, and have been marking junk mail in my inbox.  So far Evolution has failed to identify a single piece of junk mail (and I get plenty!)

Is this a sotware issue, or am I missing something fundamental? :confused:

---

### Post by Arevos on 2006-10-12
This confused me for a bit, too. You need to install a piece of spam filtering software first. One of the most popular is spamassassin, and you can install this via apt. Once this is installed, junk filtering should work automagically.

---

### Post by mediax on 2006-10-13
Ah - that would explain it! :D 

It would have been more helpful / intuitive if the Spam options in Evolution weren't enabled until anti-spam software was installed.

Thanks, Arevos.

---

### Post by bluefrog on 2006-10-13
I believe you need to train it at the beginning by flagging some emails as spam by hand

James

---

### Post by quercusrobur2002 on 2007-02-13
I too cannot get the spam filters in Evolution to work, I've been reading through the forums on this subject over the last few days and to be honest the replies are making me feel like ripping my own eyes out...

I then decided that basically if the Evolution spam filters arn't going to work intuitively, that is, without installing third party software which then has to be configured with loads of faffing about with the command line and 'piping' (whatever that means) then writing loads of complaicated filter rules, I'd go back to using Thunderbird with its nice simple 'mark as junk' options like I used to when using Windows XP... So then I discover I've got to jump through a whole load more hoops in order to export all my emails and addresses frm Evolution to Thunderbird, installing yet more third party software it seems.... I'm getting tired, ratty and irritable and my inbox is still full of spam...

Is there any really simple way of just getting the Evolution spam filters to 'just work' that a Ubuntu (its for 'human beings' after all, remember ;) )newbie can sort out without their brain melting down and oozing out of their ears into a congealed puddle in the corner????

Sorry about the tone, but this Evolution thing is really getting irritating....

(PS, I have indeed installed spamassassin and Bogofilter, and ticked the boxes under the 'plugins' menu in Evolution, makes not a blind bit of difference. I did the thing about labelling a load of legit emails as 'junk', then relabeling them as 'not junk' again. Total waste of time. The spam still sits there in my inbox refusing to move until I remove it by hand.)

---

### Post by Strider42 on 2007-02-15
I would guess once you have Spam in your Inbox you will have to move it manually, but once the Spam filters are set up correctly it should then take care of all other incoming Spam mails.  Well that is what happened with my setup at. least.

---

### Post by quercusrobur2002 on 2007-02-16
Nope. I have to mark it all by hand, it then gets moved to the junk folder, but this is no better than just deleting it.

---

### Post by meng on 2007-02-16
I didn't install any additional software, but at the beginning I had to mark certain emails as junk, after collecting a few hundred of these, Evolution 'learns' which messages to move to junk (but you also have to watch out for legitimate emails that get moved to the junk folder). If you ever clear out your junk folder, Evolution 'unlearns' all of this.

No spam filter is perfect, so learn to live with it.

---

### Post by quercusrobur2002 on 2007-02-16
Um, I could do without your somewhat snide 'learn to live with it' reply, which isn't actually helpful or addressing my issues, my point is, my evolution junk filter is not working. I've either followed or been utterly confused by advice I've so far recieved from these forums on this particular issue, help and advice on other subjects has thus far been exemplary and got me out of many a fix. I was going to switch to Thunderbird but now I feel its becoming a point of honour that this evoltution issue is either fixed (ie, a user friendly 'just works' spam solution is enabled via Evolution's 'mark junk'option) or else ubuntu acknowledge that they need to rethink their 'Linux for human beings' tag if non-intuitive non-spam filtering Evolution continues to be its default email 'solution'.

I don't want to make an issue out of this or flame anyone, I would just like a intuitive spam filtering option that doesn't end up with me tearing my own eyes out with frustration and still finding that NOT ONE SINGLE BIT of spam has been filtered and wondering why I spend i good 10 minutes of my mail checking time hand filtering spam when Thunderbird just deals with this garbage.

---

### Post by meng on 2007-02-16
Apologies. I was trying to help you, but I won't make that mistake ever again. I was underlining the fact that no filter is perfect, and did not mean to be snide or otherwise offend. Never mind, you are now on my ignore list so I won't respond to any of your questions again, not even by accident.

However, I will reiterate _my_ experience that if you move messages to Junk and leave them there, after you collect enough messages, Evolution sees patterns and filters based on these. I have never installed a plugin. I was silly enough to delete the junk messages once, and Evolution had to start learning how to filter all over again. But I'm not smart enough to explain why *your* experience is different.

---

### Post by Mr Nick on 2007-02-16
I find it extremely difficult to understand why some instructions are so terribly confusing, but it is not something I think is worth getting someone pissed off at me.

I purposely set the settings so that evolution will not receive any mail. I send a lot of emails every week, and like it when I am not bothered with spam. Thunderbird takes care of the spam for me.

---

### Post by TwistesdTexan on 2007-02-17
I use Thunderbird and the spam filter on it is pretty good. No extra software. It does have to learn also but it seems like the learning curve was real quick.

---

### Post by quercusrobur2002 on 2007-02-17
Sorry Meng, I had 'slightly' overimbibed last night, I need a personal filter that stops me sending emails or contributing to forums once I've passed a certain alcohol intake level (hey, now theres an idea, maybe somebody could come up with a bit of software that links input (beer) with outut (ill-considered emails)), I regret misunderstanding you, hope theres no ill feeling... I do actually appreciate peoples help and advice but am finding the particular brick wall of Evolutions spam filter, and the fact that despite following all the various bits of advise not ne single spam has been filtered out, frustrating.

But will persevere, its all part of the learning curve, so they tell me...

---

### Post by Kateikyoushi on 2007-03-04
Man in this aspect evolution needs to evolve a lot to keep up with TB, Do I really have to keep hunderds of spam on my machine for the spamfilter to work ?

---

### Post by Kateikyoushi on 2007-03-04
> **TwistesdTexan said:**
> I use Thunderbird and the spam filter on it is pretty good. No extra software. It does have to learn also but it seems like the learning curve was real quick.

Not mentioning I do not have to keep the spam on the machine for the filter to work.

---

### Post by bratliff on 2007-03-04
I have installed filters for evolution. It is not a matter of the filter not doing as much as I would like. It is a issue of not working at all.
The filters are enabled in plugins but do not show up on any menu.


bob

---

### Post by quercusrobur2002 on 2007-03-08
I currently have 1280 spams in my junk folder, all marked as 'junk' by hand, Evolution still has not automatically picked up a single one...

---

### Post by deresh on 2007-03-09
i have the same problems. i have gived up on spamassasin and installed bogofilter package.

then i have enabled bogofilter plugin in evolutiona and DISABLED SPAMASSASIN plugin and now it works like a charm :)

---

### Post by Roger_Melly on 2007-03-09
This may not be of great assistance but if it is let me know.  I have paid (not a hefty fee) for mailwasher.  It is a very easy to use pre evolution device that allows you to view and delete/bounce and so forth your mail before it leaves your server.  I think the code is open source but you are paying to filter through the mailwasher database or something.
It was a bit difficult to find the right version but i did eventually.  If you are interested I can post more...

Do you have to point spamassassin to one of these ere filter thingamabobs for it to work?

I had a go at downloading it but couldn't even find it once I had!  that's how rubbish I am at the moment!

---

### Post by WKnew on 2007-03-11
I too find that marking things as junk didn't seem to result in future success at filtering spam. Fortunately for me I don't get the amount of spam that some here have posted. Oh the interesting part. 

Here is the interesting part: I added my yahoo mail to Evolution and didn't set up a message filter for it like my other two mail accounts. The result ... 2 out of 3 spam messages have been filtered automatically without any manual marking as junk. Interesting indeed?

---

### Post by kevmartin on 2007-03-26
I had the problems too - till I tried the method in [This Thread]("http://www.ubuntuforums.org/showthread.php?p=2355058#post2355058")

Weird, but it workedREALLY well :)

---

### Post by Stephen Shellard on 2007-04-10
Peace brothers (or sisters as the case may be.)  I have a great deal of sympathy with  quercusrobur2002  in this discussion for Evolution filters have todate not worked for me.   I started by ticking the boxes to activate spam filters;  this didn't work;  then I installed bogofilter and spam assassin;  this didn't work even though I have embarked on a long and patient training process.  Doubtless I am getting it wrong in someway or have overlooked something obvious to a more trained user.  However, I am sure that meng has had a different experience and by some curious permutation his straightforward approach has worked painlessly.   In the circumstances it will be hard not to betray just a little frustration with those such as myself who continue to get it wrong.  There is plenty of testimony on the formus however to suggest that Evolution junk filters are just a little less than user friendly.

I note  however in another thread on the forums  [http://ubuntuforums.org/showthread.php?t=354040&highlight=evolution+junk+filters](http://ubuntuforums.org/showthread.php?t=354040&highlight=evolution+junk+filters)  that there is fresh hope for those like myself who have had a rather bitter experience of Evolution junk mail filters;  I am still trying this out so can' t yet testify to the quality of the advice and note that if you read down the thread there is still some unhappy customers but in general the noises from this thread seem encouraging and well worth a try.

---

### Post by quercusrobur2002 on 2007-04-11
I followed the link to the thread suggested by kev martin above and actually got the sapm filter working at last!! I'm still having problems in that the sapm filter is now rather too over-enthusiatic and filters out quite alot of genuine mail as well as spam, so I still need to regular check my psam folder to fish posts out of the garbage, but this is still infinaitely preferable to the earlier situation that was causing me so much angst and rage...

But Evoltion developers could certainly do with making the whole process much more intuitive, either that or maybe Ubuntu could consider having Thunderbird integrated with Calender functions (Sunbird??) rather than Evolution as the default email/calender client??

---

### Post by kyphi on 2007-04-11
I am not in a position to advise on the spam filtering abilities of Evolution but can speak with some authority on a spam filter that really works: MailWasher Pro, available for a modest fee from [http://www.firetrust.com](http://www.firetrust.com).  This programme is available for Ubuntu as well as various other distros.

I use the Windows version (because I am used to it) in conjunction with CrossOver Linux.  Crossover also runs several other Windows programmes.

Not only does MailWasher have learning filters, it does a whole lot more.  Check it out.

What I like most about it, is that I can read my emails while still on the server and decide which ones I want to accept and which to delete so that they never reach my inbox.

---

### Post by antoz on 2007-04-11
I have found in the past it is best if the spam is filtered at your server that way it never gets near my computer. In fact in the mail set up I tick leave at server and only click send - receive after I checked what is there and delete anything I don't know. Most ISP providers offer free spam filtering these days.

---

### Post by texasjim on 2007-04-21
Hoo Boy, I was just thinking about junking Evolution and going back to T-bird cause the filters don't work.  I'm not thinkin anymore, I'm goin.  Now if only I can EXPORT from Evo (everyboy imports, nobody exports), I'll leave this P.O.S. spam collector alone.

MENG: Please ignore this too.

 Jim Hayes

---

### Post by kevmartin on 2007-04-21
Spam filtering is still working great for me since I found out about the need to train the program on what isn't spam as well as what is spam ... as per:
[http://www.ubuntuforums.org/showthread.php?p=2355058#post2355058](http://www.ubuntuforums.org/showthread.php?p=2355058#post2355058)

---

### Post by quercusrobur2002 on 2007-04-22
> **texasjim said:**
> Hoo Boy, I was just thinking about junking Evolution and going back to T-bird cause the filters don't work.  I'm not thinkin anymore, I'm goin.  Now if only I can EXPORT from Evo (everyboy imports, nobody exports), I'll leave this P.O.S. spam collector alone.

MENG: Please ignore this too.

 Jim Hayes

I would have migrated to T-bird with Sunbird extensions for calender functions only couldn't find any way to easily transfer my contacts/emails/calender settings over from Evolution... Investigating this on the forums it seemed I had to install third party software, convert everything to a different format, then convert it all back to a format T-bird could read and genrally have loads of hassle and hard work. Eventually though I managed to get the filters working as per the thread linked to above...

---

### Post by texasjim on 2007-04-22
Fortunately, my last install was only a couple of weeks ago, not much in my contacts and mail except family gossip, and I have no need for calendar functions. Primarily want T-bird for it's ability to capture incoming addresses and it's junk filtering.

Y'all keep a strain on it...

Jim

 Here's how I got it done:
1. Configure Thunderbird
2. In T-bird go to EDIT-ADVANCED-CONFIG EDITOR
3.set FILTER to INCOMING and press enter
4. mail.collect_email_address_incoming will show, use right click to toggle to TRUE.
5. In Evolution forward any inbox mail and any saved mail to yourself.
    Also in Evolution Contacts send your individual contacts to yourself.
6. Start thunderbird and get your forwarded e-mail.  
7. Use the list of your contacts you mailed from Evolution to complete your T-bird address book.
8. Takes a little time, but no 3rd-party stuff involved.
9. Thunderbird will start filtering your junk as soon as you tell it what is junk one time.

Jim

---

### Post by luis borges on 2007-06-17
My procedure from scratch:

1. sudo apt-get install spamassassin
2. enable spamassassin (just follow instructions during install)
3. enable junk control on evolution (if not already checked)
4. **disable bogofilter plugin**
5. mark as junk your spam (notice "learning" at left bottom in evolution)

Tip: if you have already marked junk mail, then copy all that junk to your inbox, select it, and mark it again. (notice "learning"...)

Hope this helps.

---

### Post by lisati on 2007-06-29
My own preference is for a "challenge/response" system.  The down sides to this approach, however, is apart from adding to email traffic when the filter doesn't recognize an incoming email address, some of the people I know are pretty clueless when it comes to understanding instructions like "I don't recognize your email address.Do***_ this_***, to make sure your email gets through to me otherwise I won't see it." - they just hit "reply" instead of following the instruction.

---

### Post by masingerz on 2007-08-05
the problem with using thunderbird is that when I click on a doc on the desktop and i right clilk "send" the defualt email client is evolution...not thunderbird, im giving a shot to spam assasing, and luis borges post  ill tell you guys how it goes

EDIT: I followed the steps luis borges gave and it works very decently, for other users, please remember this is a linux system, of course we want ubuntu to be user friendly: 

linux is user friendly, it just chooses who he is friends with.

---

### Post by eudemus on 2007-09-17
What I ended up doing in Evolution / Gnome was as follows:
(And the latest version of Evolution is annoying since it doesn't allow you to select options when piping to bogofilter)

1. create a separate local folder for Spam (this is important, cos you need it to be stored as a separate mail file (which the standard Evolution spam isn't).

Your best bet is to manually put a load of definitely spam messages in there, and run the following from the terminal to train the filter.
bogofilter -Ns < /home/jamie/.evolution/mail/local/Spam

2. Set up Filter on Incoming mail:
Pipe to program /usr/bin/bogofilter
does not return 1
Mark as spam, stop processing.

3. Using the Session Manager, set your system to run the following on every login:
bogofilter -Ns < /home/username/.evolution/mail/local/Spam
or
bogofilter -s < /home/jamie/.evolution/mail/local/Spam
(the first is safer than the second, because everything in the Spam folder is "deregistered" as non-spam and registered as Spam. So, just in case anything got wrongly classified through bogofilter as ham on a previous occasion, this will correct that. This should mean that you help to train bogofilter whenever you put something manually into your Spam folder)
This training command will then run whenever you log into Ubuntu (GNOME). It retrains bogofilter based on the entire contents of your Spam folder.

Hope this helps. (I've actually switched to KDE desktop now, and am running a similar thing in KMail - which is slightly easier, and has a nice wizard that configures this all for you.)

Cheers
Eudemus

---

### Post by philinux on 2007-09-17
Since I changed my email address I get no spam and I only register my hotmail account on sites requiring an email registration. 
Just my 2 p's worth.

---

### Post by kenny1948 on 2007-12-13
I'm not concerned with receiving junk mail, I'm worried about sending junk mail.

I just got a message from Roadrunner, my ISP security department telling me that an inordinately large amount of spam has been generating from my computers address.  I know I'm not sending this stuff, and it must be some sort of trojan horse.

What I need to know is this.  I thought Linux OS was immune to such stuff.  So how do I find something like this lurking on my hard drive?:confused:

---

