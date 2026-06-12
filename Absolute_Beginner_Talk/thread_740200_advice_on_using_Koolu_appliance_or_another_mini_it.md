---
title: "advice on using Koolu appliance or another mini itx pc"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by greavette on 2008-03-30
Hello,

I'm trying to figure out which would be the best hardware to use.  Here's what I'm trying to do:

Use Small fanless PC -> install Ubuntu Gutsy (Hardy) -> run Windows XP under vmware

I've found two PC's and can't decide which is the best to use.  The two PC's I'm looking to use are:

1.  Koolu fanless mini pc Specs:
Processor: AMD Geode LX 800 (500MHz at 0.9W).
Chipsets: North Bridge - embedded in Geode LX South Bridge.
Memory: 512 MB (1 x 200-pin DDR400 SO-DIMM).  I will upgrade to 1 Gig of Ram.
[http://72.14.205.104/search?q=cache:42ZqW9RVO0kJ:www.koolu.ca/Who-is-KooluCA/Koolu-Specifications.html+koolu&hl=en&ct=clnk&cd=32&gl=ca&client=firefox-a](http://72.14.205.104/search?q=cache:42ZqW9RVO0kJ:www.koolu.ca/Who-is-KooluCA/Koolu-Specifications.html+koolu&hl=en&ct=clnk&cd=32&gl=ca&client=firefox-a)


2.  VIA EPIA CN10000EG Fanless Mini-ITX
Processor • 1.0GHz VIA C7 nanoBGA2 Processor.
Chipset • VIA CN700 North Bridge.
• VIA VT8237R-Series South Bridge.
System Memory 	• 1 DDR2 400/533 DIMM socket.  I will upgrade to 1 Gig of Ram.
[http://www.minipc.ca/index.php?main_page=product_info&products_id=1111](http://www.minipc.ca/index.php?main_page=product_info&products_id=1111)


Ignoring price, I'm hoping someone can give me some advice on which board could handle more easily running Windows XP through VMware on top of Ubuntu?

I'm thinking the VIA EPIA fanless PC is more robust and will be able to run both OS more smoothly, but  I really like these Koolu PC's and was hoping they could handle my requirements.

Any thoughts are greatly appreciated!

Thank You in advance.

---

### Post by saj0577 on 2008-03-30
[www.mini-itx.com](www.mini-itx.com) another good site

I woudl say number 2 to be honest mate, but if you have the money i would maybe try to get a better processor.

Saj

---

### Post by twright on 2008-03-30
why not put vmware server + win XP on an other computer on your network then just use the client on whatever you buy

i doubt there are many small fanless PCs that could run XP natively let alone as a vm

---

### Post by greavette on 2008-03-30
Thanks very much for your replies.  

twright - Are you saying to use a more robust PC, install VMware Server and run Windows XP...then use my small fanless PC to connect to the more robust PC and run Windows XP that way?  Maybe through VNC or some other method?

Just to give a bit more information, I'm using 8 of these small fanless PC's in an office environment that connect to a 9th PC.  The 8 fanless PC's are for inputting data into a database on the 9th non-fanless PC.  The 8 fanless PC's and 9th non-fanless PC are all connected to each other wirelessly.

Do you think this would work having a big Server running 9 virtual images of Windows XP and have the small fanless PC's connect into each virtual image?  Would having a wireless connection be a very bad idea?

Wow!  This has gone in a direction I never thought of.  

I'd appreciate to hear more your thoughts...Thank You.

---

### Post by twright on 2008-03-30
yes,
there is no need to use vnc. vmware server comes in 2 parts server and client, although most people put them on the same PC they can be in where ever you want (just put the ip of the server in instead of 'localhost')

such a setup would work but you would need quite a powerful server and it would probable be easier to use ethernet for the server rather than wireless (it requires quite a bit of work to setup wireless in terminal) but the clients could be connected however you like

i have a basic ubuntu server + vmware setup at home (mainly to stop my laptop getting so hot while running VMs)

---

### Post by saj0577 on 2008-03-30
Also i would recommend ethernet as well if it is possible, is the need for 8 pcs because you will have 8 people working at one time or is their another reason?

Saj

---

### Post by greavette on 2008-03-30
Well, I've just spoken to the owner of this business.  I've voiced my concern over wireless before and he has now agreed to my wired solution.  I had been working on convincing him a wireless solution introduces a wink link into his network so I'm very happy to drop the wireless now.  I will be building this now with a wired ethernet solution!  

The 8 PC's are at workstations where various data is input at the same time.

I've been using VMware server for about a year now and it never dawned on me to take a better look at it when I start the application.  Now that you mention it, there is an option to run a vmware image on a remote PC.  I've never done this before, but will be learning it very shortly. I'll have to explore this option a lot more to cost out a bigger PC to house all the images, but it does make sense.  I could lower the requirements on the small fanless PC's and keep the network wired.  I was worried about having an image on each fanless PC and having to manage each image..I like the idea of managing the images on one PC only.  In the event a small fanless PC fails and needs to be replaced, there is less work to be done to get the windows image back up and running again!

Thanks again for your help on this.  I really appreciate it!

---

### Post by twright on 2008-03-31
it's just a matter of installing the client on the PCs and imputing the ip of the server, i think the remote image options are something else
 
you will need at least 2-4Gb of RAM on the server and a resonably fast CPU (my 5 year old server at home can handle arround 6 VMs runnings at once)> **greavette said:**
> Well, I've just spoken to the owner of this business. I've voiced my concern over wireless before and he has now agreed to my wired solution. I had been working on convincing him a wireless solution introduces a wink link into his network so I'm very happy to drop the wireless now. I will be building this now with a wired ethernet solution! 
 
The 8 PC's are at workstations where various data is input at the same time.
 
I've been using VMware server for about a year now and it never dawned on me to take a better look at it when I start the application. Now that you mention it, there is an option to run a vmware image on a remote PC. I've never done this before, but will be learning it very shortly. I'll have to explore this option a lot more to cost out a bigger PC to house all the images, but it does make sense. I could lower the requirements on the small fanless PC's and keep the network wired. I was worried about having an image on each fanless PC and having to manage each image..I like the idea of managing the images on one PC only. In the event a small fanless PC fails and needs to be replaced, there is less work to be done to get the windows image back up and running again!
 
Thanks again for your help on this. I really appreciate it!

---

### Post by greavette on 2008-04-01
Hello twright,

I just had a thought this morning about another way to set this system up that may be a bit easier.  Since I'm now thinking of running all VM's off of one big computer, I may as well put Edubuntu on this big PC, and have my client workstations boot into Edubuntu.  Each thin client would then use their own Windows VM and I can manage the whole shebang from the one PC instead of having to remote into the client workstations for upgrades and fixes.

I can still use the Koolu machines (but I'll get the Thin Clients instead...same as the appliance but with no hard drive)
I'll build a bigger PC (Quad Processor, 8 Gig of Ram)

I've tried Edubuntu last year with an old PC as my thin client.  It worked and I was able to remote into the Edubuntu server without error.  On the Edubuntu server I wasn't able to get the option to view the clients that were currently being used, but maybe with Gutsy (and very shortly Hardy), this will work a bit easier for me.

I suppose I should make sure my Lan can handle the traffic...maybe upgrade to Gigabit?

So, any comments on whether using Edubuntu would be a good idea?

Thanks.

---

### Post by aeiah on 2008-04-01
why edubuntu? why ubuntu at all? why even linux? what is it you plan to do no the linux platform besides launch a windows xp vm?

---

### Post by greavette on 2008-04-01
Hello aeiah,

That's a fair question.  

This business has bought specialized software for their business.  This software runs only on Windows.  They have client workstations around the office where they input data into a database.  They've asked me to help them out (I'm friends with the owners) and it sounded interesting to me so I said sure.  Their business is very far away from me (8 to 9 hour drive from where I live), so I wanted to create a solution whereby I can support them and make it easier on myself in the event a problem occurs.

Being so far away means I have to solve for many things possibly going wrong.  What if the Windows O/S fails?  What if the PC (hardware) fails?  How do I fix the O/S or PC quickly and easily without having to totally re-install the O/S and load back this specialized software.  I also don't have the option of jumping in a car to drive up and fix it (I have a day job and family).

So I came up with the following:
So I thought I would use a Virtual Machine (and take a backup of this VM) and run their client workstations from a virtual machine.  In the event the Windows O/S fails, I can quickly delete the offending VM and copy in the backup. If the PC (hardware) fails, I can buy a new PC and take the backed up images and put them back and send the PC to them already configured.

I enjoy running Linux at home and thought that using these Virtual Windows XP images ontop of a Windows Operating system means they have to buy an extra license.  If I use Linux (I prefer Ubuntu) then I can save them the cost of that license and run the VM's off of Ubuntu.

So basically the main reasons why I'm looking at an Ubuntu solution to run this Windows only system is so I can backup and restore their client workstations in the event a problem occurs and to make it easier for me to support them in the event a problem occurs.

If someone can give me reasons not to use VM's on Ubuntu (or Edubuntu), I would be very happy to hear from you.  Although I have an idea in my head on how to make this work, I'm very appreciative to hear other people's thoughts and views.

Thanks!

---

### Post by aeiah on 2008-04-01
of course, im not against linux in the workplace, and the only reason i cant push it at my office is that we use AutoCAD a lot. we have open office and linux servers running fedora though at least :cool:

but i was wondering why you dont want to just install windows on the clients. dont you still have to buy all the licenses if you host them as a VM on the server?

since all the machines are the same, if a client falls over, you can have a disk image of the xp install ready to roll. i know this would mean physically being there, but that server is gonna be under a lot of strain serving the database, all the virtual machines, and the roaming profiles for all the windows clients (i dont even know if you can set up roaming profiles without windows server)

so i think both have advantages and disadvantages.

as for the edubuntu thing, if you're only using linux to run a virtual machine, then you should probably go for something as light as possible. ubuntu server (since these things obviously work well with ubuntu) and perhaps not even a desktop environment on top; just xorg with vmware player running in fullscreen, or just fluxbox or something.

---

### Post by greavette on 2008-04-01
Hello,

Yes, regardless of my solution, they will have to buy an individual Windows license for each VM to run their client software.  I thought of just installing on each client machine, but they really want to use a small mini type PC that doesn't take up much real-estate on their desks (maybe even attach it to the back of an LCD monitor) and I was having trouble finding a mini PC that was robust enough to run Windows that didn't cost a lot of money.  Plus as I've said...the big thing I have to worry about is support for when problems occur.  Plus, showing them a Linux solution, as long as it works, is a great way to promote Linux!

Do you mean using Ubuntu Server with LTSP so the Thin Clients can remote into the Ubuntu Server and run their VM's?  I didn't know you could run VMware Player with just xorg?  Can you point me to instructions on how I would set this up?  I'd be very interested in learning about this as well.  I like to have many options for a solution and I too was worried that the main Server would be under a lot of stress with all these VM's running at the same time.

Thanks!

---

### Post by aeiah on 2008-04-01
i dont know if you can without a desktop environment, but if you can you probably should, because it just adds extra weight to the clients. if you have to have one, id suggest using ubuntu server and running fluxbox, openbox, or another super lightweight desktop environment, since you only need it so you can run vmplayer full screen.

---

### Post by greavette on 2008-04-01
Ahhh, now I see what you are saying...thank you for the advice!  
I'll try running a lightweight desktop on Ubuntu Server, install LTSP and PXE boot the thin clients to the server to only run their VM's.  Sounds like a good idea to me.

I've got a lot to play with here.  I really appreciate all the help with this thread!

---

### Post by twright on 2008-04-01
i would think that LTSP and vmware together wouldn't make much sense as they would both basically be doing the same thing so the load on the server and the connection would be more than doubled

i suggest you just install plain ubuntu/xubuntu on the clients (fluxbox is much lighter but not as easy to use) and let that connect to the server.

have you tryed the needed applications under wine? if they work you could save a lot of effot and just go with LTSP.

---

### Post by greavette on 2008-04-03
Hello twight,

Sorry for the delay in responding.  Thanks for your insight.  I didn't think of the load that would happen if both Edubuntu and VMware were passing data back and forth to the Thin Clients.

We won't be moving to a Gigabit lan so I think my only options would be to:
1.  Leave the VM image on the small PC and run it from there.
2.  Keep all my imaages on a larger PC and use VMware Server to connect to the image.

Thanks again for all your help!

---

### Post by twright on 2008-04-03
i would recommend putting all the images on the server so you can back them up more easily

then just put an easy to use lightweight linux distro on the clients with vmware server client (you can make a custom liveCD for easy deployment) and that is all you need to do

make sure you secure the server though

---

### Post by greavette on 2008-04-07
Hello Again,

I've been a bit busy this weekend so I apologize for not responding sooner.

I do prefer keeping all the images on 1 PC which will make backup much easier for me so I will pursue this option. 

Thanks again for all your suggestions.  Since this thread has moved away from it's intended purpose, and seeing as I have many more questions after I've decided upon a solution of the hardware, I should really list what I'm doing hardware wise and open a new thread [http://ubuntuforums.org/showthread.php?p=4668048#post4668048]("http://ubuntuforums.org/showthread.php?p=4668048#post4668048")  asking questions about the software and how to build a Server PC for all my VMware Server images.

Here's the scoop:

I've decided to buy the following mini-itx boxes to hang on the back of an LCD monitor (VESA):
[http://www.logicsupply.com/products/vm7700](http://www.logicsupply.com/products/vm7700)
They are a little pricey compared to the Koolu, but they are more robust than the Geode and after speaking to the Logic Supply sales, they are lighter than other VESA mounted PC's.  I can upgrade the Ram to 1 Gig if I need too.

As for the Server, I'm looking at either buying a System 76 Server or a Dell.  

Thanks!

---

