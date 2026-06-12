---
title: "Add a new PPC mirror to repositories"
date: 2011-05-12
forum: Apple Hardware Users
---

### Post by clarissa.w on 2011-05-12
Hi there

AARNET ([http://mirror.aarnet.edu.au/](http://mirror.aarnet.edu.au/)) now has ubuntu-ports. ([http://mirror.aarnet.edu.au/pub/ubuntu-ports/](http://mirror.aarnet.edu.au/pub/ubuntu-ports/))

I was wondering whether it could be added to the mirrors/repositories list.

Could anyone tell me how to manually add it to my computer via software sources.

I am interested in lucid PPC ubuntu ports.

Thanks

---

### Post by jerrycal on 2011-05-12
> **clarissa.w said:**
> Hi there

AARNET ([http://mirror.aarnet.edu.au/](http://mirror.aarnet.edu.au/)) now has ubuntu-ports. ([http://mirror.aarnet.edu.au/pub/ubuntu-ports/](http://mirror.aarnet.edu.au/pub/ubuntu-ports/))

I was wondering whether it could be added to the mirrors/repositories list.

Could anyone tell me how to manually add it to my computer via software sources.

I am interested in lucid PPC ubuntu ports.

Thanks

sudo gedit /etc/apt/sources.list

sudo apt-get update

or: 
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Repositories%20in%20Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Repositories%20in%20Ubuntu)

---

### Post by clarissa.w on 2011-06-03
Attached is a screenshot from my computer.

AARNET is not working.

Thanks

---

### Post by Jared Norris on 2011-06-03
Gday,

It's Jared from the HUMBUG list,

When you say it's not working what sort of errors are you getting?

If you can run ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal and then paste the output with the error message that will help track down what the issue is.

---

### Post by clarissa.w on 2011-06-04
Hi there

Attached is the text from the terminal when typed

sudo apt-get update && sudo apt-get upgrade

Thanks

---

### Post by Jared Norris on 2011-06-04
The fact that EVERY repository entry (both aarnet and all the others) are failing it is almost suggesting to me that it's a DNS issue.

Can you go back to your terminal and type ```
ping mirror.aarnet.edu.au
``` which will check if your DNS is resolving the address. If this works we can look into other ideas. If this gives you errors your problem is with DNS not the repositories.

---

### Post by clarissa.w on 2011-06-04
Hi

I entered it into the terminal. See the attached text file for details.

Thanks

---

