---
title: "wine download"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Clive Richardson on 2007-12-09
Adding the WineHQ APT Repository: I've managed to open the 'terminal window' and pasted the information into it. But I cannot work out how to add the repository to the system's list of APT sources.
Please bear in mind that I am not clever with computers but, of pension age, am determined to get away from windows. So I didn't know what a 'terminal window' was but found the info through  google. So please use very basic words. Many thanks:

---

### Post by Orivel on 2007-12-09
Well which repository to add depends on the version on Ubuntu you are using.  To find this, click on "System" in the top left hand corner and then on the drop down menu click "About Ubuntu".  A window will open with lots of information about Ubuntu.  A few lines down it will say "Thank you for your interest in Ubuntu...."  This will tell you what version on Ubuntu you are using. Could you post this so then i can tell you which repository you require.

---

### Post by Clive Richardson on 2007-12-09
I have version 6.10

---

### Post by Orivel on 2007-12-09
Ok then, open up the terminal and type the following ```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list
```

---

### Post by Myglaren on 2007-12-09
> Please bear in mind that I am not clever with computers but, of pension age, am determined to get away from windows. So I didn't know what a 'terminal window' was but found the info through google. So please use very basic words. Many thanks:

Me too.
I'd recommend that you spend a few hours trawling through the advice given in these forums and also take a look  at [Psychocats](http://www.psychocats.net/).
Pearls of wisdom strewn around everywhere, invaluable resources.  Nice people too.

---

### Post by Clive Richardson on 2007-12-09
O.K. have done that.

---

### Post by rkd on 2007-12-09
Yes, psychocats looks very helpful.  In particular, I think

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

will help you deal with adding repositories using the mouse interface rather than the terminal, which I imagine you'll find more comfortable.  Have fun!  You can learn to use Ubuntu!

---

### Post by Orivel on 2007-12-09
Now in terminal type ```
sudo apt-get update
``` then in terminal type ```
sudo apt-get install wine
```

---

### Post by Clive Richardson on 2007-12-09
Orivel I'm getting lost I think. I made a shortcut key to open a terminal, as per instructions I found earlier. So I put your first line into a terminal and then closed it (with the X). Am I to type your next two sudo lines into two new terminals?

---

### Post by Orivel on 2007-12-09
Sorry, just say if i am going too fast or skipping too many steps. Open the terminal again, then type the first line and press the enter key.  When that has completed, type the second line and press enter.

---

### Post by Clive Richardson on 2007-12-09
Oh dear, should have thought of the enter key. However on pressing enter it asks for a paswword but won't let me type anything.

---

### Post by rkd on 2007-12-10
Clive,

When you enter a command that begins with sudo in a terminal, it will request that you enter your password -- the same one you type at normal login.  It won't do the command unless you successfully enter that password.  When you enter the password, you won't see anything appear on the screen while you are typing, but it really is noticing the characters you type. It just isn't giving you any indication that it is seeing the characters.  After you have typed the last character of your password, press the Enter key.  Then it will do the command, assuming you entered the password correctly; if you mistyped the password, it will ask for the password again.  When that command is done, you may enter another command, if you have more commands to do.  

Some directions I have read say that the computer remembers that you have entered your password to sudo for about 15 minutes, so I guess that if you enter another sudo command within 15 minutes of entering the first one, it won't ask for your password again, but I'm new to Ubuntu and I haven't done that myself, so I don't know whether I'm understanding that point correctly.

You mentioned that after entering the command that Orivel gave you earlier into the terminal, you closed the terminal using the X.  I guess you mean that you didn't press Enter after putting the command in and before clicking the X.  If so, I think you stopped the terminal without having it do the command, so I think you may need to do that earlier command now before doing the two that begin sudo apt-get. (You can do all three in the same terminal.)

---

### Post by Clive Richardson on 2007-12-10
Thank you, that worked and it does remember the password. 
Have the followimg message after the 'update'entry:Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
and after the final entry:WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? 
Any ideas?

---

### Post by Clive Richardson on 2007-12-10
I have been to the psychocats site and read up on using the Synaptic Package Manager and have sucessfully downloaded WINE in spite of the 'not authenticated' warning which others seem to ignore. 
So I would like to thank everyone who helped me as I feel I have learnt a lot and am a little more confident as a result.

---

### Post by rkd on 2007-12-10
I'm glad you were able to get Synaptic to work.

The warning messages, in case you are curious, look to me to be saying that the package installer was not able to do the check to verify that the package you asked it to install matched what the package provider said they published (the signature could not be verified, where "signature" means something like a summary of the file made just to be used for such verification purposes).  

The purpose of the check is both to make sure that the package was not accidently changed during the transfer to your computer and to make sure that no one has intentionally substituted a malicious version of the package for the proper version.

In looking at a web page I found by doing a google search of the text of the error message, I found some directions to use a couple of commands that seem to be obtaining and installing the public key from budgetdedicated that is needed to do that verification.  I guess Orivel just forgot to include those commands in the directions he gave you.

The chance that skipping the verification will cause any problem is low, so installing WINE without doing the verification probably won't bring you any trouble.

---

### Post by v.alari on 2007-12-10
Holy way better way to install dependencies batman! Tried installing Wine in Synaptics and wouldnt do binfmt, terminal added it by default. This was fortunate considering I didnt have binfmt in my synaptics list

---

