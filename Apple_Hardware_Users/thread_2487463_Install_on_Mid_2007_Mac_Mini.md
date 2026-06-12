---
title: "Install on Mid 2007 Mac Mini"
date: 2023-06-05
forum: Apple Hardware Users
---

### Post by james-donahue158 on 2023-06-05
Hello all,

The title almost says it all.  I'm trying to install Ubuntu Cinnamon on my old Mac Mini (mid-2007).  I can get the machine to boot from the USB.  I can also start the install process.  For approximately 10-15 minutes, what appears to be a progress bar (not really, it's just a sort of flashing line) displays, saying the installation is taking place.  Then, it stops and says installation failed.  

Anyone else have a similar experience and a solution?

Thanks.

---

### Post by QIII on 2023-06-05
Moved to ***Apple Hardware Users***

---

### Post by guiverc on 2023-06-05
I have no useful experience on MAC hardware, thus I can only provide *generic* comments.

You didn't provide any release details; which to me matter significantly. There are differences with the ISOs for each, thus this detail provides useful detail; plus if you're talking about a LTS release which has different kernel stack choices (*and for some, different versions of installers included on the media*) more detail is provided.  I suggest you provide that detail.

If I had release detail; I'd look up what installer existed on your ISO, I don't so cannot. I'll assume it's a `ubiquity` installer (as seen [here]("https://cdimage.ubuntu.com/ubuntucinnamon/releases/lunar/release/ubuntucinnamon-23.04-desktop-amd64.manifest") for 23.04).

I'd switch to text terminal and explore what the system is doing... Did you verify the media before you started the install? (*again release matters here and you didn't provide that detail*), but I'm betting you are using media that self-verifies, thus I'd explore for the success message before starting an install (*I've written about it [here]("https://askubuntu.com/questions/1311183/do-i-need-to-check-the-integrity-of-a-ubuntu-install/1311209#1311209") & elsewhere*). Beyond the media checks I'd normally do before the install was started; they can provide clues as to what the system is doing regardless of installer (*though I do find the snap installers a little harder due to confinement, but clues are still there*).  Did you look? If the install crashes, system logs provide clues.

---

