---
title: "linux"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by richard willacy on 2005-12-15
name richard 

got ask this question, does btbroadband do linux software for there voyager 105 adsl modem and if so where can i go to download it from and if i put it into my cd drive when using linux  will the ubuntu know its there and will it work,but if
thats no good then im stuck,whats the best option to go about getting my modem working,i know that people on this site 
dont have the same modem as i do,but what sort of modems are good for this linux and if some one has got theres 
working can you please tell me what there modem is and may be i will get one so it will work with my setup because at 
the moment  i cant get anything working,i have followed what peolpe on this website have said but nothing works and 
i kmow that a lot of people are having good times with there set up are i the only one who is having this trouble or is 
this modem trouble causing trouble for lots more, if i was having a good time with my ubuntu linux i know that i would help 
this poor man by telling him the modem i have and it works brilliant and the make and model then he would be able 
to go and buy one and thats it all woking fine, any help on this subject well i thank you richard

---

### Post by Mustard on 2005-12-15
I'm not on adsl myself so I'm not really sure.  I take it that the voyager 105 adsl modem is a USB modem?

I have heard there are some issues with USB modems.  I would look into getting a modem that uses an ethernet connection rather than a USB connection.

Below is a link that covers a lot of differernt hardware that is supported in some fashion by linux.

[http://www.tldp.org/HOWTO/Hardware-HOWTO/](http://www.tldp.org/HOWTO/Hardware-HOWTO/)

---

### Post by bscbrit on 2005-12-15
Richard,  one suggestion is to install 'eciadsl' using synaptic or apt-get, whichever you prefer.  It provides drivers for the bt voyager USB 100 series modems.  I do not think that BT provide their own package yet, but have you asked them?  Even if they don't have one, they might think of producing one if enough people show an interest.
I have always found that external serial connected modems work best for linux unless you want to buy an ADSL modem/router.  The latter is, in my experience, the best option although it might also have other features which you do not need.  The modem/router also often allows you to share you adsl connection with other computers, but only you can say if this is important for you or not.
Have you tried Googling for 'linux bt voyager modem' for example?  You might find something useful - this link looks promising:

[http://www.maxpc.co.uk/tutorials/default.asp?pagetypeid=2&articleid=28069&subsectionid=707](http://www.maxpc.co.uk/tutorials/default.asp?pagetypeid=2&articleid=28069&subsectionid=707)

which quotes

"BT currently supplies the BT Voyager ADSL modem to home customers. The first version was problematic with Linux, but now works well. For these modems, you need a driver package called ECIADSL. This is designed to support almost all ADSL modems which are based around the Globespan chipset. This includes the BT Voyager, as well as devices from ASUS, D-Link and some USRobotics models."

I use a D-Link DSL-504 but there is probably a more up-to-date version of the modem available now - mine is several years old!  But it is simple to set up and 'just works'.

---

### Post by bscbrit on 2005-12-15
Richard

How this this sound to you?

[http://www.broadbandstuff.co.uk/product_info.php?products_id=219&osCsid=7a95ba7ee231b982f7ace23be043e162](http://www.broadbandstuff.co.uk/product_info.php?products_id=219&osCsid=7a95ba7ee231b982f7ace23be043e162)

If you do buy this, or something similar, you will find that the 'ethernet' connection will probably be much easier to install than the 'USB' connection - this particular model has both.  Ethernet is much better supported in Linux.  USB is getting much better but, as you have found, there are still a few gremlins in the system.

---

### Post by bscbrit on 2005-12-15
Or this....


[http://www.broadbandstuff.co.uk/index.php?cPath=149&osCsid=7a95ba7ee231b982f7ace23be043e162](http://www.broadbandstuff.co.uk/index.php?cPath=149&osCsid=7a95ba7ee231b982f7ace23be043e162)

After the forums, Google is probably your best friend.

---

### Post by richard willacy on 2005-12-15
thanks for the threads about this modem problem,

mustard
bscbrit
 thanks for your comments on the modem,but i like the links to this shop which shows these modem
but can you please tell me how one works a little if you dont mine,because im thinking of getting 
one of these modems,hope there not usb modems and how do you connect on to your computer and
will the ubuntu breezy know its there and will it work, i want to know as much as possable about 
how these modems work anything is better than my voyager usb 105,the modem i have is not working right 
it keeps stoping all the time and another thing is do you get this scware box like thing on your pc screen
its always there on the left hand side and when i go onto the ubuntu website there it is real pain in ass,
anyway than you very much richard

---

### Post by bscbrit on 2005-12-15
Richard
The adsl modem/routers are really quite simple to use but you cannot  expect to open a box and it suddenly burst into life.  But you seem to have managed to set up your bt voyager in windows and it is no more difficult than that.  First of all, you must have a computer that has an ethernet connector.  Most modern motherboards do and, if yours doesn't, then a PCI ethernet card costs about &#163;10.00.  Yes, you can always find one that costs a lot more but with care you needn't pay much more than I have suggested.  But I stress, many modern computers already have an ethernet connector on the rear.  Your computer handbook will tell you which one it is if you are not sure - it looks like an overgrown telephone connector.
An ethernet cable is used to connect the modem/router to the computer.
The modem/router is probably no more difficult to set up than your original modem but you have to collect some information first.  Some of the information will be in the handbook that came with the bt voyager (because you will still be connecting to the same ISP, simply using a different modem), and some of it will probably be in the connection data held in windows.  I haven't got a bt voyager so I cannot describe exactly where it is because I cannot replicate your system.
You connect the modem/router to your telephone line using exactly the same cable as you currently attach to your bt voyager, including using the microfilter.
You almost have at this point a working network.  But the computer and modem/router must use IP addresses to talk to each other.  The modem/router will probably come with a default address already set up - again, until we know which model you buy, we cannot tell you precisely what it will be (probably something like 192.168.0.1 but it will depend on what you buy).  The manual will provide this information.  The computer has to be told the modem's address and the computer itself must be given an address.  This is very easy to do but would take quite a lot to explain in a meaningful way without you being able to use that information immediately.  However, if you purchase such a device come back to the forums and someone, myself if I am around, will talk you through it.
Honestly, it is not difficult and will be easier for me to explain than trying to set up your bt voyager modem over this forum.
I would also recommend that you try to contact someone in your area who is also a linux user.  I am assuming that you live in the UK (because you are using btbroadband!) but I could be quite wrong.  There are lots of LUGs (linux user groups) around the UK and there will probably be another linux user living near you.  It is simply a matter of finding him or her.  I think you will find it reassuring if you can find someone nearby to talk to and to perhaps provide some practical help if it is required.  Many people can tell you what needs to be done over the internet - but, at the moment, only you can do it.  Finding help nearby might be something you will want to consider.  If you Google ([www.google.com](www.google.com)) for 'LUG UK' for example, it will give you lists of LUGs around the country.  Find the nearest and try to get in touch with them.
You might also find some help at the shop where you intend to purchase the modem/router.  Explain what you are trying to do and you might get some assistance - the worst they can do is say 'No' (and you can always take your money somewhere else if they are rude about it).  But, they are there to sell items and not fix your computer so don't expect too much.
When you first started with computers, you probably found Windows a bit difficult to use.  However, you also probably soon became familiar with how to do what you wanted.  It is the same with Linux, including Ubuntu.  Of course, there is a mass of information on the internet - but your modem problem makes that less useful in your particular case.  So you might find yourself coming back to these forums more than some others.  That is not a problem providing you are patient.  All the people who provide help here also want to use their computers and they give some of their time to help others.  Sometimes you will post a question and not get a very quick answer.  You can help yourself here however,  by making it clear what you wish to know.  For example, this thread is called 'linux' which is the title you chose when you started the thread.  That did not actually tell anyone else anything about your problem and quite a few people are very good in specialist areas.  If they had seen the words 'USB modem' they might have jumped in to provide some help but 'linux' - well we are _all_ using linux.  This is not a criticism of you, I am simply trying to explain why you may not always get as much help as you would like.  In short, don't lose hope.  It might sometimes be tempting to throw away linux and go back to Windows but, believe me and all the other users here, if you persevere it is well worth the time and effort that you put into it.

---

