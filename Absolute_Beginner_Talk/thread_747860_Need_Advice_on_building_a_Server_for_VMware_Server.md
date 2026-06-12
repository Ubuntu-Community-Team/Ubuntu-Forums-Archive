---
title: "Need Advice on building a Server for VMware Server"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by greavette on 2008-04-07
Hello,

I thought I would start a new thread since my old thread ([http://ubuntuforums.org/showthread.php?t=740200](http://ubuntuforums.org/showthread.php?t=740200)) of looking for a mini-itx morphed into a discussion about my solution to run multiple Virtual Images.  Anyway, I digress...

Basically I'm asking this forum how hard it would be to setup a VMware Server PC to handle 6 VMware images using Ubuntu as my Host O/S?  Management of this Server PC is done remotely (I'm very far away and anyone near this PC cannot really help me).  I'm new to using Ubuntu (since Feisty) and have very little knowledge of the command line (except what I copy and paste from forum threads).  I'm not even sure if it's possible to run VMware Server without a GUI? 

Now to give you more detail of my setup:

I have in an office environment of 5 client workstations running Windows XP that input data into one database on a seperate (6th) PC (again running Windows XP).  I've been asked to help out this business, but I live many hours away and cannot jump in my car to support them when a computer fails.  So I thought I would use Virtual Images for each client workstation and the database PC.  In this way I can backup each image and in the event a problem occurs, I can remove the failed image and copy back a backed up image.  On the advice from the thread I referenced above, I think it would be a good idea to have the following configuration:

[LIST]
[*]5 client workstations use small mini-itx VESA mounted to LCD.  These will run Ubuntu Gutsy and have VMware Server installed.
[*]1 Larger Server PC will have some kind of Server O/S running with VMware Server again installed.  This PC will house the 5 Windows XP client workstation images as well as a 6th Windows XP image with the database software (LIMS software is being used here).
[*]The 5 mini-itx PC's will use VMware Server remote host to remotely connect to their images on the larger Server PC.
[/LIST]

I have many concerns, and I'm hoping someone has some advice for me on how best to set this up:
[LIST]
[*]I have limited Linux experience.  I have been using Ubuntu since Feisty came out, but only for surfing, mail and setup of some remote software (Hamachi, vpnc, vnc, and VMware Server).
[*]I am looking to implement a solution for this office sometime in early to Mid May 2008 (depending on how long it will take to get the hardware setup and O/S configured).  Am I crazy for thinking I can work this all out by then?
[*]Since I want to run all VMware images off of one PC, I'm concerned about what Host O/S to use.  I could use Ubuntu Server and install VMware Server,  but I've never used Ubuntu server before and my test to connect to a remote host for a VMware image failed.  Before I put this into place I will off course test it out here at my house, but I'm wondering if I'll bite off more than I can chew.  I'm more familiar with Windows since I've used it for so long so I keep leaning toward taking the easy route and buying a PC with some kind of Windows O/S on it that can handle running many VM's.  Cost isn't really an issue here (within reason of course), so if I have to buy another Windows license for the Host OS then that's fine.  The thing is I really enjoy working on Ubuntu and I am willing to learn more about how to use it. I'm just worried that I'll run into some problem controlling these VM images on Ubuntu Server from so far away.  
[*]Since I haven't decided on which Host O/S software I should use, this has caused me to waffle on which Server to buy.  I've found a website called system76 which sells preconfigured Ubuntu servers.  This is ideal since I don't want to waste time trying to find the right hardware to work with Ubuntu.  Plus their Servers have Raid hardware controllers built right in to help with backing up data and an option for battery backup (this is very important to me as well to have a current backup of the images in the event a hard drive fails). 
[*]My the other option I'm considering is buying a Dell Server with some kind of Microsoft O/S on it.  This would be more familiar to me which might make things easier?  Maybe I'm wrong.
[/LIST]

Some details on the specs for each hardware (in case you are interested).  Based on the amount of Ram each image will need and the hard drive space for each:

[LIST]
[*]Each client PC image will need 750 MB Ram
[*](Lims) Database image will need 2 Gig
[*]I thought my Server PC should also have for itself 2 Gig (just to be safe).
[*]Total Ram required is:  7.75 GB of Ram
[/LIST]

[LIST]
[*]Each client PC image will need 25 GB of drive space
[*](Lims) Database image will need 100 GB of drive space
[*]I'd like the Host O/S to have 80 GB of drive space.
[*]Total hard drive space required is:  305 GB
[/LIST]

I will be backing up each image in the event an image fails.

I apologize for the long winded thread starter.  I've been reading up on all sorts of things I feel I need to take into account here...securely remoting into the main PC to manage these VM's.  I've now tried connecting to my Ubuntu box with VMware Server remote host, but it says it was blocked (so I've been reading up on how port 902 is blocked in Gutsy).  How to best backup all this data (which is why the Raid configuration from the System 76 PC intrigued me).  If you can't already tell, I'm feeling a bit overwhelmed!   I know I'm asking a lot here, but I'd appreciate any help you can provide in helping me make a decision.

Thanks!

---

### Post by twright on 2008-04-07
you should be able to get it up and running very quickly but you will need to use the terminal to do everything on the server side

first step is to install vmware on the server by running
```
sudo apt-get install vmware-server
```(you will need to enable the canonical partner repository in /etc/apt/sources.list). you will also need to give the server a static ip [http://www.sematopia.com/?p=50](http://www.sematopia.com/?p=50).
then install fluxbuntu, puppy linux, DSL or similar on one of the clients. you can then download the client from here:
[http://download3.vmware.com/software/vmserver/VMware-server-linux-client-1.0.5-80187.zip](http://download3.vmware.com/software/vmserver/VMware-server-linux-client-1.0.5-80187.zip)

just install that and then you can open it by running 'nohup vmware-server-console' on the client. you will then be presented with a screen asking you for the servers ip address, enter it, your username and password (i recommend you create an account on the server for each client) and you will have a normal vmware screen from which you can setup the virtual machines as you would normally

also don't forget the CPU requierments, i would recommend something with at least duel core maybe even quad.

for secutity encrypted LVM might be necessary.

---

### Post by greavette on 2008-04-08
Hello again Twright,

Thank you for being so patient with me...even when I begin to freak out and rant like I did in my original post.

I have some testing to do ahead of me to make sure I'm comfortable with all of this.

So I would use a static IP for the server so that the command on each client to remote host into the Server would be the same...except each client would have it's own account...that's a great idea!  What would each account see when they connect to the host?  Would they see all 6 virtual images, or is there a way to just display the image they need to use?  

If I use a static IP for the this vmware server PC, what type of networking should I give to each of the XP virtual machines the clients will use, Nat or Bridged?  The database image consists of Windows XP with SQL Server running that each client PC connects to over a network...I think this would mean each client image would need it's own IP in order to connect to this virtual Lan.

I really like the System76 Servers.  Their customer service is excellent.  I also like the fact I can buy a server with Raid 10, hot swap cage and Dual Redundant Hot Swap 650 Watt Power Supply.  I'm thinking the Quad Core 2.13 GHz with 8 Gig of Ram should be enough.  It's not cheap, but this is for a business and their data is really important to them so  I don't want to leave anything to chance!

For anyone else interested in this thread...I also found this blog on building your own vmware server PC for around $900.
[http://duartes.org/gustavo/blog/post/2008/03/20/Building-a-quad-core-server.aspx](http://duartes.org/gustavo/blog/post/2008/03/20/Building-a-quad-core-server.aspx)

Like I said, I have a lot to test (and learn!) so I'll take your instructions and try it out.

You really have a lot of patience twright and I really appreciate all the help you've given me!

Thanks!

---

### Post by HermanAB on 2008-04-08
Well, six VMs at the same time is a bit optimistic.  You can have as many VMs as you want on disk, but running them all at the same time is a different matter.  Two or three yes, six no - unless it is a big machine with a quad core processor and oodles of RAM.

Cheers,

Herman

---

### Post by twright on 2008-04-08
you would need to use bridged networking

i think that by default vmware lets each client see everything but you could probably manually set the ownership of the images using chmod and chown (sudo chown -R *[user name]  [image directory]* then sudo chmod -R 200 *[image directory]* )

my 5 year old server (2Ghz, 2Gb RAM) can run 4 VMs simultaneously but these are linux VMs so they are more lightweight and i don't know how well this would scale. a similar server to that mentioned in the blog should be more than enough to do the job.

if you have some old PC's i recommend you try doing it with one server and one client just to check everything works.

---

