---
title: "Sirius/sipie Problem"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by chperry on 2008-03-28
I am running Ubuntu (Gutsy). I have sipie installed and working! Now the problem. It plays for 5 to 10 minutes (2 to 3 songs) and then simply shuts down. I restart sipie and it works fine for 5 to 10 minutes. Any ideas?

Running x86_64

I am completely new to Linux, btw.

Thanks

Charles

---

### Post by timetoballj on 2008-03-30
i have sipie installed but cant i get it running do you have any tips

---

### Post by chperry on 2008-03-30
I read through the entire thread linked below and then installed based on what was recommended:

[http://ubuntuforums.org/showthread.php?t=284893](http://ubuntuforums.org/showthread.php?t=284893)

As I said, mine only works for relatively short durations before stopping at random.

Charles

---

### Post by BobbyIceCubes on 2008-04-01
It is because when you ran the initial installation your Sirius information was not saved properly. Re-install the program, and follow the instructions in the Sipie directory. Once this is done, it will never sign off, or ask if you are still there. I had this same issue, I hope this helps!  This is where I obtained the information on the install.  [http://markjstevens.net/?p=13](http://markjstevens.net/?p=13)  I have had no issues on "2 different machines", and trust me " I suck when it comes to CLI ".  Here are some snapshots I posted: [http://www.ubuntux.org/sirius-satellite-internet-stream-thanks-to-the-sipie-application](http://www.ubuntux.org/sirius-satellite-internet-stream-thanks-to-the-sipie-application)  This is a snapshot of the song notification:  [http://www.ubuntux.org/sipie-song-notification-sweet](http://www.ubuntux.org/sipie-song-notification-sweet)  When I was finished I right clicked on the desktop and created a Application Launcher, and used the following syntax: /usr/bin/sipie.py (should be the usr/bin directory under your user id) And if you know this I am sorry, again I suck at CLI and installed it in the wrong place).
Once this was done I grabbed the ICON from one of the folders in Sipie...

More very helpful information at the following location with regard to the MPLAYER you use located here: [http://sipie.sourceforge.net/](http://sipie.sourceforge.net/)

Pronounced SY PIE, like "sirius python", sipie is a on line player
for Sirius online Internet streaming. It requires a login to 
Sirius's streaming, and both guest and subscriber logins are 
supported. It provides the a back end and a cli and gui.

To install in Ubuntu

Make sure mutliverse is enabled, if not enable it
    grep multiverse /etc/apt/sources.list

if nothing returns go to System -> Administration -> Synaptic Package Manager
        Settings
        -> Repositories
        -> Ubuntu Software
        -> Software restricted by copyright or legal issues (multiverse) 
            CHECK THAT

then 
    # python-wxgtk2.6 is option but it currently works better then the pure
    # gtk interface
    apt-get install mplayer python-setuptools python-wxgtk2.6

    # easy install sipie
    easy_install sipie

---

### Post by chperry on 2008-04-01
Thanks for the response.  That is actually the steps I followed originally.  It took my username and password and I was able to enter the odd word that popped up.  I do not get any kind of error.  It just stops playing.  Is there a way to kill the file (whichever one that is) that is caching my password so that it will prompt me for it again?

---

### Post by BobbyIceCubes on 2008-04-02
First, just a quick question. Do you click play again, and it restarts playing the music? I will get the information for you this morning regarding clearing your password file. I have to ask one of my colleagues who is a linux god (keeping in mind that I suck at CLI) ;-)
I was trying to replicate the issue last night for hours, and I found that on an older Dell P600 laptop with a wireless 802.11B card it pauses on occasion. But if I click on play again, it continues. Now on my HP 802.11N & G wireless cards on 2 other devices, or here in the office on my 5 year old  Dell Dimension 8200 I do not have this issue at all with wireless 802.11G. What I am trying to do is isolate it down to hardware such as my wireless router running in N, G, B compatibility mode verses locking it down to one frequency such as G or N. I am convinced it is not the Sipie program itself, or** Ubuntu 8.04**. 
How I came to this was odd, I had the System Monitor open, and I noticed that my network history was looking like my fathers EKG indicating network disconnect... I do not see this on my other machines, the network bandwidth for the most part remains constant. So with that said I want you to try something... Under "applications" then "system tools", and open the "system monitor" prior to opening Sipie. Notice the snapshots I have attached from 2 different machines. The first one plays the stream flawlessly, the second one is where I have duplicated your problem. _I tested this with nothing else open, and update manager closed as well._ If you do not have wireless, it could be the drivers of your nic card...  I have noticed that some NIC cards are set to auto, auto for speed and duplex. Some networking devices do not like this, so I would make this static.  keep me posted....

---

### Post by BobbyIceCubes on 2008-04-02
The config file you are looking for is hidden and so is the directory, so make sure that you go to "view" and display hidden files. It is located in your home directory home/.sipie/     <<<< File name is "config"****
The contents of the file will look like this if you crack it open in the txt editor:
try to delete it, if you edit it a backup is created.

[sipie]
username = Th0rzHamm3r    <<<(Fake)
login_type = subscriber
canada = False      <<<<When you answer this next time remember case sensitivity****
bitrate = low
cryptpass =4xxx852cxxx36ddefxxx2c68b29a   <<<(Fake as well)

---

### Post by chperry on 2008-04-02
Once it stops, I click play again and it runs fine.  Last night it ran for about 20 minutes before it died.  I will try your idea on checking my bandwidth.  I do not use wireless, but I am sharing the modem connection with two other computers.  I guess it could be network traffic problems nic card issues.

Thanks for your help btw.  I need all I can get.

Charles

---

### Post by BobbyIceCubes on 2008-04-02
Charles,

Anytime... I am no rocket scientist at this either, but I will say that this is the longest I have run any flavor of Linux without blowing it up... According to my mid-year review, for my "stretch goal" (to me: defined as an unobtainable goal) I need to learn "new technologies"... I guess this would be it...
Cheers...  Bob

---

### Post by timcredible on 2008-04-02
not sure what sipie is, but i tried sirius'  free trial a while back, it worked without any extra programs.  i'm an xm subscriber, and their site works fine for listening online.  you do have to remove totem and install mplayer though, because for some reason totem doesn't work for these.  if sirius has changed their player requirements in the last year, then just ignore my post.

---

### Post by chperry on 2008-04-02
How do I check my NIC settings and how do I change them?  My network stream looks like your second example.  

Charles

---

### Post by BobbyIceCubes on 2008-04-03
Charles, I locked the duplex, and speed on my router...  It will not accept connections less than 100/Full...

---

### Post by BobbyIceCubes on 2008-04-03
Tim, I find that very interesting. I tried everything. I do not even have totem installed. Sipie was the only solution that I found after searching through countless blogs, and support groups. The one good thing with Sipie, is that you only have to log on once. It has never asked me for any credentials, or the crypto key after the ID and password since it is saved in a file. Could you send a snapshot if it working?

---

