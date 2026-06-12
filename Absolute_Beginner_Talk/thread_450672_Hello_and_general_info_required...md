---
title: "Hello and general info required.."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by terri0204 on 2007-05-21
I have never heard of Ubuntu - however i have been in the IT field for many years.  After researching some solutions (shadow server) for SOHO i was directed in the the direction of this OS.  I am also working on educating SOHO that there are other options out in the IT other than MS.  I do have knowledge of UNIX or Linux -  what i would like to do is use Ubuntu as a backup server for a BETA version at my house to see how it works and how it plays with other OS.  From what i have read, it sounds like this program would work and provide security.  Is that true?  Can I install Ubuntu as the server on a host, then have Ubuntu as the back up server and proxy for the net?  Other host systems would be XP Pro and SuSE.  My original plan was to use the new SOHO server that MS is trying to sell to the public.  However, I really would like to get away from that.  TIA for all your info and comments...:p

---

### Post by Happy_Man on 2007-05-21
I guess.... so long as you know how.... :)

---

### Post by Mr.Beast on 2007-05-21
> **terri0204 said:**
>   I do have knowledge of UNIX or Linux -  what i would like to do is use Ubuntu as a backup server for a BETA version at my house to see how it works and how it plays with other OS.  From what i have read, it sounds like this program would work and provide security.  Is that true?  Can I install Ubuntu as the server on a host, then have Ubuntu as the back up server and proxy for the net?  

Hi Terri0204, 
Welcome.  You'll notice by my beancount that I'm quite new here, but you'll find that this is probably one of the most helpful places around in terms of attitude.  :-) 

Firstly Can I just say, and I hope you don't take offence, but I'm confused in relation to some of your terminology in balance to your experience?  I only say this as I don't want to offend by pitching real tech speak and maybe scaring you off, or by dumbing things down too much and getting shot down!.

Ultimately the answer is going to be a YES, Ubuntu would be able to tick most, if not all of your boxes, but I think it is also fair to state that most other Linux distributions would as well! (You mention SuSe)

That said here is my take on your request.
Ubuntu is a flavour of Linux rather than a program that you run (this is the dumbing down bit I refer to!)
I'm not sure what you mean by a BETA version, Edgy Eft version of Ubuntu seems popular and stable, Feisty Fawn (7.04) is what I'm using at the moment, but not in real anger as it were and this also seems stable on a day to day basis (lol, but then, so is XP ;-)

I'm not aware of the Shaodw server that you are talking about?? (I'll be reaching for a bit of google about this one later.) 
I assume that you are doing your SoHo work as part of a business venture.  Good for you to investigate other options that are out there other than MS.  Personally speaking I think that this is exactly the right area that the open source community should be targeting in most areas.

Firstly and perhaps this can opent the door to those with more experience with  Ubuntu in these areas than I. So perhaps they can chip in with applications and links to specific How-Tos? I think that we need to ascertain what tasks you are expecting to do with Ubuntu at home and potentially in a SoHo environment.  

Proxy server you've mentioned. (This seems quite radical, or rather higher up the list in terms of Soho requirements I would say in my opinion but I guess you have a specific requirement.)

Backup server.  A good Idea.  I personally would have a cheap hardware raid option (Mirror) and back things up to that, then once a month, plug an external drive in an archive / migrate to this media and move offsite. ( Are you going to run dedicated backup software for this purpose? and does it have Linux and Windows clients?) Make sure that Ubuntu can get the best throughput out of any tape devices you may decide to attach.


Mail server:-  I am sure that there are applications out there that will happily sit on Ubuntu and carry th standard post office functions for a small business.

File storage, Print Spooling.
To get any XP client to store files on a linux, or unix server you will pretty much require either SAMBA running on the Linux server, or an NFS client for Windows (or similar) Samba is well used throughout businesses already in production environments, so I'd probably say that this would be your best bet. ( You could even get it to be a Domain controller to authentic your XP clients if you like.)  But it should eat this sort of thing for breakfast.

Now, personally, (only in a corporate environment) I have not had the best experience with CUPS / Linux print spooling for XP clients. Others with more experience please chip in on this aspect.

Security, I'll probably get shot down for saying this, but Ubuntu is more secure out the box than XP, or other microsoft operating systems , True Fact. No dissagreement there, however I would say that it is no more secure than a well built XP installation. (Removal of all extraneous services running, sensible use of groups and users and permissions. 

In terms of weighting against microsofts latest offering.  I have two stances. 
1) This new version, in the office, forget it.  I wouldn't put it in I would rather put in a full MS solution, or a linux, than a chopped about version. (He he, I may change my mind on this one)
2) In the Home.  Nope, Windows XP Media centre with the right software and bits could do everything that I would require from a server edition (In fact, oh.. It is,  right now in fact.)   I would rather spend the money on a SoHo GB switch and up my LAN bandwith so that it can really stream HD content. (Wouldn't reccommend this in a business environment for obvious reasons.)

---

### Post by terri0204 on 2007-05-21
Hi and TY,


NP -Firstly Can I just say, and I hope you don't take offence, ...down!.  No offense taken!  And my back ground is as such - teacher at a college in Information Systems Analysis, I hold certs :lolflag: in Cisco, MS and CompTia.  The people (teachers) that i work with believe in teaching Cisco and MS - we do do a bit is SuSe.  As to the word BETA I was thinking of MS.  Before i go out to client i like to make sure program play nice together.  I'm trying to bring open source into our college however, feel like I'm hitting my head against the wall.  So I hope that helps explains geek speek and then using dumbing down some of my terms.  

I want to be able to present other options to our students and that is why i was looking into Ubuntu and i also work w/SOHO in ref. to security (work in doc office and such).    

The shadow server/backup server - I was looking at MS new server platform for soho and in one of the blogs a person said that MS was on the right track, however, he was already doing this with Ubuntu.   

As to the backup server, w/Xp you can set the clients to keep the data on the server - so if they delete you can do a quick restore (as in restore from previous versions - prop tag) however, most SOHO dont have the man pwr or the knowledge to set this up - let alone the money.  And from what i have read Ubuntu should be able to to do this?  And w/that said u dont have to mess w/ any RAID confs. 

"Mail server:- I am sure that there are applications out there that will happily sit on Ubuntu and carry th standard post office functions for a small business." Had not thought of this...good point.

thank you for your posting and sorry for not being a bit clearer - i was coming from the posting from and for more than one reason.  and i also wanted to see if a NOOB would get flamed on this site.  A lot of sites say they dont - but do....

---

