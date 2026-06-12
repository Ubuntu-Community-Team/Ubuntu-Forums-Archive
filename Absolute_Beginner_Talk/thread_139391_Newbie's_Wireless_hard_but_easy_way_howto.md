---
title: "Newbie's Wireless hard but easy way howto"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by Peacepunk on 2006-03-03
Keywords for you people using search engines

Sony Vaio subnotebook vgn t16sp wifi wireless laptop

Tech refs: full name of my computing device is PGC-4C7P, with
NetCard intel PRO/Wireless 2200BG
WiFi Box Linksys BEFW154 (802.11bg)
OS Breezy Badger

This howto adresses mistakes during steup rather than incompatibility of material

You'll need:
- A WiFi Box, obviously, preferably with DCHP (not Mandatory)
- another computer with access to your WiFi box administration, 
-knowledge on how to change the Setup of your WiFi box, 
-the laptop (most probably, or WiFi-ed device) put besides, 
-and your UBUNTU install disk.
-A Working Internet connection

If other computers are using this WiFi box, you'll need knowledge of their respective network configurations & modifications - this won't be addressed here.

My issue: I did something wrong during install, so connecting was tricky, unstable if available at all.

Let's get to it: Prepare to re-install, back up your files & configs from faulty computer!

At early stage of the install, ubuntu asks for Network Setup Data.

Retrieve them using your other PC. Print out and safeguard Setup Data (Gateway, Ip's and so on, DCHP should fail). Check in the WiFi Box Wireless security department, for the type of encryption: You MUST have WEP only enabled, for now at least.

**Note: Unsecured, all security Down is something I tried also, It failed as well**

On the WiFi Box I choosed a 64-bit encryption, and wrote down the resulting Hexadecimal 10 digit code provided by the WIFI Box in a safe place. Lynksys allows you to write a keyword and click on "generate" to get your resulting 10 digit Key. Save your setup and get out of the box-online admin system

Back to Ubuntu Install:
Choose WEP
I recommand Hexadecimal (I tried Passphrase, didn't work for me)

Simply write down the Hexadecimal, 10 digit key from the box in the imput field where Ubuntu explains you all the ways your Key may look like. it will look like 

nnnnnnnnnn


**Note; This ain't the most refined way, one can do better, safer, I am aware of that. We are in Newbie's world here, and so am I)**

If you have a DCHP-Capable box, network will be retrieved OR you will know you have a Driver/Hardware issue.

If you know you do not have DCHP, or DCHP fails, now Ubuntu will ask you (after some screens) if you want to set it up manually. Grab the printed Setup from your WiFi Box, and give it a try, imput every nnn.nnn.nn.n that are being asked

**Note: Naming of these fields are not necessary straightforward, they sometimes differ between what Ubuntu is asking and how a Linksys box names them. Trial & error process here, it took me two times only to figure it out**

Until you good, ckick on Back when Ubuntu fails, and retry as long as you are sure your WiFI card from the computer is good, your internet ISP isn't down, and your WifiBox working.

**Note: You can verify the presence of your WiFi Computer as Emitting in the "MAC" addresses department of your WiFi box. Sorry, I will not enter into details here, I only know how to check in my Linksys Box & recommand you use Mac Filtering if available**

END

Once again, I, a newbie, was lost in all that encrypted setup stuff. The above "hard Way" comes from the fact that any changes in network setting I was making when Ubuntu was running were instantly forgotten as soon as I closed the Net Setup Dialogue, switching back to the (wrong) input I give during Install Setup - So, no useable internet.

As a basic, intended to be easy to follow HowTo, I would appreciate fellow posters who'd like to contribute to keep it simple. 

Please, only comment if I made a huge mistake, thanks. I would update the post in such case.

---

