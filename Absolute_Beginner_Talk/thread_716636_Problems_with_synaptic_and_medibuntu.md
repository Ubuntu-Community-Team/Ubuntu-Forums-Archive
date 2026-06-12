---
title: "Problems with synaptic and medibuntu"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Alephlex on 2008-03-06
Hi,

I ran into problems trying to install Skype using the Medibuntu Repository.

I followed the instructions here:
[http://technical-itch.co.uk/2007/09/...ype-on-ubuntu/](http://technical-itch.co.uk/2007/09/...ype-on-ubuntu/)

I started feeling that something went wrong midway through using the terminal window to get the medibuntu package. I was prompted for my password which I entered. I was then returned immediately to the command promp.After that I tried to get the GPG key for the medibuntu package. That returned the following message: no valid openPGP data
found.

When i next tried to open synaptic, I got the following message:
E: type '--18:19:50--' is not known on line 1 in source list/etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache-> open () failed, please report

I am running Gutsy Gibbon Ubunto 7.10 on a Fujitsu Lifebook S7110.
Can anyone please help?

Please excuse me if the post is amateurish. I am a total newbie. And could you please help by giving me very simple instructions because I know next to nothing about where to find basic stuff in Linux. I will be trying to get an education on this soon.

Also, my keyboard seems to be responding in a funny way. I might be in the middle of typing when all of a sudden, my cursor gets shifted to a different line on the page (about 3 lines up). Is this a problem with the keyboard driver? The characters are all recognised ok and the keyboard layout is correct.

Thanks for your help in advance.

P.S. I originally posted this in the installations page but I realise that it is probably more because I am a newbie and did something wrong. So I'm reposting it here. Sorry

---

### Post by Arthur Archnix on 2008-03-06
My advice to you is to remove the medibuntu repository, download and use the latest version from skype's website (they have a deb there for Feisty, but I use it on Gutsy and it works a treat). You'll see a link for the beta with support for video. 

To remove the medibuntu repo, just type:
gksudo gedit /etc/apt/sources.list
Look for the line with medibuntu on it then put a # in front of it. Save and close. Then:
sudo apt-get update
That should finish with no errors.

Download the deb from skype (google skype for linux) and when it asks you what you want to do with it, say use gdebi to install.. 

As for your keyboard, you're probably just hitting the touchpad. You can disable it while typing following these instructions [here]("http://ubuntuforums.org/showthread.php?t=617478"): Just scroll down to number 5.

---

### Post by hyper_ch on 2008-03-06
well, there's obviously something wrong with your medibuntu sources list:

'--18:19:50--' --> that does not belong in there.

---

### Post by Alephlex on 2008-03-06
I'd like to thank you all for putting in your suggestions.

After running the rm code to remove the references to medibuntu, my synaptic manager started performing normally again.

Repeated attempts with the medibuntu repositories produced the same result as the original post

So I eventually solved the problem by by-passing the medibuntu repositories and doing a direct download from skype.com itself. The programme is now up and running and synaptic works fine too.

Thank you all for taking the time to help.

---

### Post by plucky on 2008-03-07
Alephlex,

I think you should add the **Medibuntu** repositories as well so that you can get the updated versions as they are released for Ubuntu.

To do so see [here](https://help.ubuntu.com/community/Medibuntu)

Good luck

---

