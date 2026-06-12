---
title: "Strange problem with Synaptic Package Manager"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Hurricane on 2006-12-04
Hi,
I have just installed firestarter, apart from that no system changes.

When I try to open the synaptic package manager, I get the following error:

E: Malformed line 3 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


I also now get the following error when trying to open add/remove programs:

Failed to check for installed and available applications
This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

Top right next to the clock I see the orange star telling me there are some updates available.  When I click this however, a window flashes open for a brief split second, and disappears.

I'd appreciate any help you can offer.
Matt

---

### Post by tbroderick on 2006-12-04
Did you try running sudo apt-get update from a terminal?

---

### Post by sdude on 2006-12-04
TESTING, ignore message :)

---

### Post by Hurricane on 2006-12-04
Ignored above ;)

Thanks for the reply.  I tried apt-get update but got an error.

I have just commented the entire contents of the offending file, and then apt-get update worked.

Thanks again
Matt

---

### Post by iconmichael on 2007-07-24
I had the same problem and this fixed it for me.

sudo apt-get -f install

---

### Post by Foxmike on 2007-07-24
> **Hurricane said:**
> Ignored above ;)
 
Thanks for the reply. I tried apt-get update but got an error.
 
I have just commented the entire contents of the offending file, and then apt-get update worked.
 
Thanks again
Matt
 
Commenting the offending line is just a workaround that will effectively work, but it will disable some repositories... can you post the offending line so that we can check out why it is offending, correct the problem to the source and then re-activate that repository for you?

---

### Post by mikewhatever on 2007-07-24
> cat /etc/apt/sources.list
Post the output of the above. If you comment out every line of sources.list, you won't have access to any updates and any software.

---

