---
title: "How to install hydranode?"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by ikilledclown on 2006-06-18
I get this with most programs, anyway, I downloaded hydranode because amule woudln't connect and I dont know how to install it its a .tar.bz2 file, and when extracted has a folder with a various files, do I have to use the terminal to do this? and if so how?

I'm new and don't really have a clue how to do these things!

---

### Post by u.b.u.n.t.u on 2006-06-18
When you say aMule wouldn't connect, do you mean no connection or do you mean a low id?

If it is no connection change your ports to something like this:

2xxxx TCP
2xxxx UDP

x = any number.

So you will have a port like 21234.

That will hopefully bypass your ISP if they have the standard ports blocked.

If you can access the network but get a low id let me know and we can look at setting up your router and firewall correctly. 

As for hydranode, you may be best asking at their own forum.
[http://forum.hydranode.com/index.php](http://forum.hydranode.com/index.php)

---

### Post by ikilledclown on 2006-06-18
It's not actually connecting at all, but where it says 'no connection' in the bottom right hand corner it also says 'kad: off' I was wondering if that would be anything to do with it.

Does it not matter what the other numbers are at all in those connection boxes because I simply put
TCP - 21234
UDP - 21234

Wondering if I may of done something wrong there as well.

Cheers

---

### Post by u.b.u.n.t.u on 2006-06-18
* Please keep the time difference in  mind between the UK and here. That is why I seem to be missing for 8 hours - sleep lol.

I got your PM.

"TCP - 21234
UDP - 21234"

They should not be the same.

eg:

TCP - 21234
UDP - 21235


Here is some theory, as I don't know your setup.

aMule needs a good internet connection. Good as in if you have a router, that it is set up correctly, and good as in your ports aren't blocked by your ISP, and good as in your firewall is set up correctly.

Let's start with the router (I don't know what you have but lets proceed with everything). You should find a DMZ option there. Yes, DMZ as in the miltary lingo "De-Militarized Zone". That basically opens all ports to the specified computer. That is what I do as I have an aMule box.

The other option for your router is to open the ports manually. You can do this individually for each port or specifiy a range of ports eg 20000 - 20010 and your three aMule ports are within that range, you only needed to specify TCP and UDP as the "UDP port for extended sever requests (TCP+3)" is assigned automatically.

So that is the router set up. You already set up aMule with your ports. Here are a few examples of what I might choose, to give you a better idea.

TCP - 21210
UDP - 21220

TCP - 23330
UDP - 23340

TCP  - 262626
UDP - 262636

I like to space the ports out but that is just my perference.

So with your aMule and router set up you should get a connection, albeit a lowid perhaps.

You should ideally connect to one of:

"DonkeyServer No1"
"DonkeyServer No2"
"DonkeyServer No3"

As they are the largest servers at this time.

So with everything nicely setup in aMule (I better mention put a tick in the following or you will be spammed,

Preferences > Message Filter

Tick the top 2 boxes. Servers have bots that spam or some very bored people doing it lol).

Now to your firewall. Install and set up Firestarter if you haven't already.

Under the "Policy" tab add these entries.

Allow service Port For
Unknown TCP everyone
Unknown UDP everyone
Unknown TCP+3 everyone

"Unknown" because they have a drop down list and aMule isn't included.

TCP etc means the actual port number, eg 232323. Remember you are working with three port numbers.

So to conclude, if you have no connection at all check that you have set up aMule correctly and that your router is set up.

If you have a lowid it is likely your router AND/OR your firewall.

Let us know how you go with all of that.

Now back to my morning cup of coffee for me.

:D

---

### Post by ikilledclown on 2006-06-19
I should of known the time difference as I was waiting to ring someone in australia that night!

Well I know have a connection, I found the list of servers and have connected to donkey server 1. But now I have no actual download rate at all. 

This is how I have my preferences/connections panel set in amule - (the attached picture)

Cheers

---

### Post by u.b.u.n.t.u on 2006-06-19
What is your ISP plan in terms of maximum download and upload in KBs?

You have it set as 10KBs down and 2KBs up. A 56K modem is about 5KB down.  Once you tell me that I can make a recommendation.

Also aMule is not bit torrent. Patience is needed and the longer you let it run the better. It takes days to download not hours.

I hope this helps.

---

### Post by ikilledclown on 2006-06-19
My internet connection is 1mb, and i only really want to use amule to download single songs, I usually use bittorent but you can't usually get single songs with it, I really want the setting to be set so as I can download single songs now and again, and get resonablely good download rates.

It's all a bit vague, but my understanding of all these setting is virtually nil!

Cheers

---

### Post by u.b.u.n.t.u on 2006-06-19
You didn't answer this question so I will ask it again. What is your download and upload speed in KBs? I need to know this if I am to recommend a setting.

---

### Post by ikilledclown on 2006-06-19
I seem to of sorted it now, I'm not entirely sure how, I went through and through your intructions and now it is working, a BIG thanks for that.

But I still have slight problem, I dont have a clue where any of my songs go, what setting is it that I have to change so I can get all the songs ito go into a certain folder, and where do they usually go as default?

Ever so sorry about my complete non undertstanding, and I really appreciate your help.

---

### Post by u.b.u.n.t.u on 2006-06-19
The path to your incoming folder is:

Step 1

/home/username


Step 2

View / Show Hidden Files


Step 3

 /home/username/.aMule/Incoming


How to change the incoming.

Step 1

Start aMUle

Step 2

Preferences / Directories


* Notes
Your temp file is where incomplete files are handled. Upon completion they are moved to incoming where they are shared by default.

Keep an eye on your share ratio under the statistics tab at the top of aMule. You want at least 1:1. Less than that isn't good for the network and also decreases your rating, meaning you will be further at the end of the queue. A good share ratio means you are more likely to get a file sooner rather than later.

Oh and you are welcome. O:)

---

