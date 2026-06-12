---
title: "Stubborn proxy settings in Synaptic"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by utilly on 2007-08-20
Hi, I have been hunting high and low for the config file that stores the proxy settings for Synaptic Package manager. I had the laptop on a network that required a proxy, so I entered the details in Synaptic>Settings>Preferences> Network Tab. Now I want them out, but they won't budge. 

Every time I try and get them out through the GUI it crashes Synaptic. I thought I would have a crack at manually editing the config file but can't find it anywhere. I'm using Feisty. I did try reporting it as a bug at launchpad but there was an error...

Thanks

Tonia

---

### Post by mikeyphi on 2007-08-20
> **utilly said:**
> Hi, I have been hunting high and low for the config file that stores the proxy settings for Synaptic Package manager. I had the laptop on a network that required a proxy, so I entered the details in Synaptic>Settings>Preferences> Network Tab. Now I want them out, but they won't budge. 
Tonia

Perhaps a silly suggestion - What happens when in Synaptic>Settings>Preferences> Network Tab you select the "Direct connection to the Internet" button followed by "Apply"?

---

### Post by utilly on 2007-08-20
Clicking on 'direct connection' to the internet followed by 'apply'... apply button stays greyed out. Then I click on Ok, nothing happens, preferences box just hangs there. I just did it now for description purposes and minimised it and when I went back to it, all writing missing, just grey boxes. 

Sorry if I didn't make it clear in the original post that doing this by through the GUI I get a crash, which is why I am trying to edit the config file manually. Although I'm new to Ubuntu, I work in tech support and have tinkered with linux for a couple of years so I'm not afraid to get my hands a bit dirty. ;)

Tonia

---

### Post by mikeyphi on 2007-08-20
This is above my pay grade!! But since you've got time on linux how about using apt-get through a terminal to purge and reinstall synaptic?

---

### Post by asmoore82 on 2007-08-20
config file is at '/root/.synaptic/synaptic.conf'

If you are getting hang-ups I would relocate its entire config folder
and start it after in a terminal to read any output.

```
~ $ sudo -s
# cd /root
# mkdir .backups
# mv .synaptic .backups/
# exit
~ $ gksudo synaptic
```

---

### Post by mysticmatrix on 2007-08-20
Synaptic has a stubborn problem of not recognizing GNOME proxy settings and also disrespecting them.

Try this:

When you have to use synaptic, make direct connection setting under System --> Preferences --> Network Proxy and then give the required proxy settings under Tools --> Preferences --> Network Tab of Synaptic. This will enable PROXY FOR SYNAPTIC ONLY

When you have to use all other apps, enable Gnome Proxy settings. Under such arrangement everything( including apt-get in terminal) works but Synaptic won't work.

---

### Post by utilly on 2007-08-20
> **asmoore82 said:**
> config file is at '/root/.synaptic/synaptic.conf'

If you are getting hang-ups I would relocate its entire config folder
and start it after in a terminal to read any output.

```
~ $ sudo -s
# cd /root
# mkdir .backups
# mv .synaptic .backups/
# exit
~ $ gksudo synaptic
```

Ok, I had a look at the config file and edited out the offending articles and then opened up Synaptic. I was pleased to see the settings had finally gone but when I clicked on OK, it crashed again.

I understood that the above code would have had me changing to root directory, making a hidden directory called backups and moving synaptic... I'm not quite sure what it was supposed to do but what I got from  gksudo synaptic was the following:

'Another synaptic is running. Trying to bring it to the foreground'

I had force quited (is that a word?) out of Synaptic when it crashed... how do I purge and reinstall synaptic? Would this be the next thing to do?

Thanks for all you help so far everyone. 

tonia

---

