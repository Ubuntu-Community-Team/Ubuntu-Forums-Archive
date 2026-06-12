---
title: "Problem downloading Skype"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-01-07
Hi I have tried 3 times to download skype and the first file was only under a meg, the 2nd 1meg and the third was 1.2megs. I don't know why.

---

### Post by moma on 2007-01-07
Let Automatix2 install Skype for you.
Goto Step 5) on [this page..]("http://www.futuredesktop.org/")

---

### Post by Koybe on 2007-01-07
Use synaptic... but before you need to edit your sources. Open a terminal then :
```
 sudo gedit /etc/apt/sources.list
```

Add this line at the end of the file : 
```
 deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
```

The save and close it. Go to synaptic package manager, update and search for skype. You can now easily install it.

I hope this help.

---

### Post by rapattack1 on 2007-01-09
I am still reading the page moma sent me. I am not quite understanding it. Is it a download manager?
Is there a mirror site that I can download it from in Australia where I am? 

Koybe I did what you said but haven't finished the process for 2 reasons. One is that the line finishes as "non-free". Does that mean it is something I have to pay for? The other reason is that synaptic did something else that I didn't understand. Something about something out of date. Sorry it didn't seem important.
By the way I should of mentioned I have Ubuntu 5.04.

---

### Post by hyper_ch on 2007-01-09
I might be mistaken but I think "non-free" means that it's proprietary code and not opensource code... it does not mean you will have to pay for it.

---

### Post by Biggus on 2007-01-09
Hi dude. I think it might well be better to solve the original problem of the download not completing.

My friend, who uses a laptop, sometime has a similar problem when using Firefox 2.

Anyhow, just for you old bean, I've downloaded the Skype Debian Installer from here [http://www.skype.com/download/skype/linux/]("http://www.skype.com/download/skype/linux/")

And uploaded it to [http://www.megaupload.com/?d=J5W1ZQNO]("http://www.megaupload.com/?d=J5W1ZQNO")

You may have better luck trying to download it from here.

Alternatively, if you go into your System->Administration->Synaptic Package Manager, and then do a search for 'Skype', you should be able to right click the search result, and select Install.

(Worked for me on Edgy)

---

### Post by rapattack1 on 2007-01-09
Sjau-thanks for the info!

Biggus-Thanks I got the download!!! Hey how do I install it? I haven't done any of that yet with Linux/Ubuntu.

---

### Post by Biggus on 2007-01-09
Hmm, I'm a newb too. I just double clicked it, and some package installer thing came up.

---

### Post by rapattack1 on 2007-01-09
Thanks I got that far.....um do I extract it to.....where?

---

### Post by Biggus on 2007-01-09
Mines has a little box at the top right of the windows to install it. (with a little green tick box like in the attched pic)

It just took care of everything else for me.

Is this what you are seeing?

---

### Post by rapattack1 on 2007-01-09
Mine looks very different. Will see if I can figure out how to do an image of it.

---

### Post by Biggus on 2007-01-09
It looks as if your ubuntu is associating the .deb file extension with some program other than the one which mines is set to, the 'Package Installer'.

I'm thinking that the 'Package Installer' is not available in 5.0.4 (I've only ever used 6.10), and I don't know if theres a way for you to get it.

Have you tried installing it through the 'Synaptic Package Manager'?

Again apologies if this is an 'Edgy' only menu option.

---

### Post by rapattack1 on 2007-01-09
Um I am really confused now.
I tried to do something in Synaptic but I don't know what to do. It sees skype....I can't think of the right expressions. Skype is listed there but......I double clicked on the name skype and I got this window saying "Could not mark all pakages for installation or upgrade. The following have unresolavble dependencies. Make sure that all that all required repositories are added and enabled in the preferences. Skype: depends: libqt3-mt but is not installable or lipqt3c102-mt (>=3:3.3.3.2) but it is not installable

---

### Post by Biggus on 2007-01-09
I think you want to right click it, and select 'mark for installation', it may then ask you if you want install some other stuff, and you do, if it asks you.

---

### Post by rapattack1 on 2007-01-10
No I attached a pic above somewhere.

---

### Post by rapattack1 on 2007-01-13
Is there anyone else that can help? Is the reason I am not able to install Skype because I have Ubuntu hoary 5.04?

---

### Post by Biggus on 2007-01-13
Hi dude!

I'm still here, sorry to hear you haven't got it working yet.

Anyhow, I was looking at this page : 

[http://support.skype.com/index.php?_a=knowledgebase&_j=questiondetails&_i=188&nav=+%26gt%3B+%3Ca+href%3D%27index.php%3F_a%3Dknowledgebase%26_j%3Dsubcat%26_i%3D11%27%3ESkype+for+Linux%3C%2Fa%3E]("http://support.skype.com/index.php?_a=knowledgebase&_j=questiondetails&_i=188&nav=+%26gt%3B+%3Ca+href%3D%27index.php%3F_a%3Dknowledgebase%26_j%3Dsubcat%26_i%3D11%27%3ESkype+for+Linux%3C%2Fa%3E")
> 
What system libraries does Skype for Linux require?

Skype for Linux requires glibc 2.3.3 or greater and Qt 3.2 or greater. Even if you do not have Qt 3.2 or greater, you are still able to use Skype for Linux by downloading its static version that has Qt 3.2 compiled in. However, in this case, Skype for Linux does not integrate with your desktop theme, as it does with the dynamic versions.

This information seems to tie in with the error messages which you have been getting when trying to install it through the 'Synaptic Package Manager'

Your install appears to lack these 'files' (I'm not sure what to call them), and unfortunately, I'm not entirely sure how to install them.

Maybe some kind Ubuntu Guru could oblige you?

---

### Post by rapattack1 on 2007-01-14
Thanks for the extra info. Yeah I thought something was missing and I have no idea how to fix it. I am hoping that my Linux friend will come tomorrow and wave his magic wand he he. He will also give me some basic knowledge on stuff as it is very different from Windoze. I am loving the learning experience though. Will give that page a read and hope that some Linux Guru helps out if my friend doesn't appear. Thanks Biggus;)

---

### Post by rapattack1 on 2007-01-15
Thanks for the help everyone. My friend came over and had quite a bit of fiddling to do but the good news is it is working well and I have a skype account!:)

---

