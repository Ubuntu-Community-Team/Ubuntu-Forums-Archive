---
title: "Setting up ISP?"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by maparus on 2005-11-06
Is it possible to go on line using Ubuntu Breezy 5.10 CDLive? If so how do I set up my ISP

                                                           Many thanks maparus

---

### Post by kori.mendocino on 2005-11-06
yes, it is possible.
if your connection hasn't been detected automagically during boot-up, you'll have to configure it manually. from the top panel, choose System > Adminitration > Networking and work it out. good luck

---

### Post by maparus on 2005-11-06
When trying to set up my ISP connection I get a pop-up that says
"could not autodetect modem device" does this mean my present
modem is not compatible with Linux? If so I saw a Dial-up modem
yesterday a Stratitec model 1C56A that did say it was Linux compatible.
Would this be a good choise to replace mine with?

                                          Determined to get it right maparus

---

### Post by Mustard on 2005-11-06
Some helpful links...

[https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")

Is it a modem connecting to the external serial port or is it an internal pci modem?

Just assuming its an external serial port modem, connected to either COM1 or COM2, its going to be called for each respectively either, /dev/ttyS0 or /dev/ttyS1.  If its not detecting the COM port automatically try setting it to either one of these values manually and see if you have more success.

---

### Post by maparus on 2005-11-06
I followed the directions with no problem until I got to item #16 type your Ubuntu user account
user name. What name does it want? I tried maparus and the reply was " maparus does not exist" tried Ubuntu@Ubuntu like it says at the beginning of the terminal with the same responce. what do I put there?

                                                still determined maparus

---

### Post by Mustard on 2005-11-07
[QUOTE=maparus]I followed the directions with no problem until I got to item #16 type your Ubuntu user account
user name. What name does it want? I tried maparus and the reply was " maparus does not exist" tried Ubuntu@Ubuntu like it says at the beginning of the terminal with the same responce. what do I put there?

                                                still determined maparus[/QUOTE]

It states in the how to that those steps are only necessary for you to set up the user account so it doesnt need 'sudo' to start the modem up.  Further down it says that you can test the modem connection straight away with the command 'sudo pon'.  I read in your other thread that you were using a liveCD.  I've never tried it from liveCD, but you might try skipping down to the steps about testing your modem straight away with 'sudo pon' to connect and 'sudo poff' to disconnect.

---

