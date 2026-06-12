---
title: "ACK! Can't resize my windows xp partition :("
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by neobonzi on 2006-10-18
So I decided to install Ubuntu on my E1505 Dell Laptop because I just started college and I have to keep up with all the other nerdy comp sci major kids who have linux kernels for brains.

BUT...I have a problem.

I can't seem to resize my windows partition! I used the LIVE cd from ubuntu to try to install it but when i get to the part where I   'm supposed to adjust my partitions - i get the error message "Couldn't create a partition with enough space".

I've Defragged my computer twice, tried running the partition editor program thing (forget the name) from inside ubuntu ( which simple paused for a bit, said it was working, then went back to the screen it was at before. ).

And now im frustrated. Any advice to resizing my windows partition so i can install ubuntu on the leftover space?

Computer Specs:
E1505 1gig DDR Dual Channel ram
80 gig HD
Windows XP Home 
Ati X1400 Graphics card

---

### Post by mcduck on 2006-10-18
You could try running starting windows in safe mode and then running the defrag. Otherwise defrag won't be able to move all files and that may stop you from resizing the partition.

---

### Post by ReaderRat on 2006-10-18
The gparted (Gnome PARTition EDitor) disc is more up-to-date. than the one on the Live CD. You can get a copy at: [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/download.php)

---

### Post by Bachstelze on 2006-10-18
No need to mess with it, the gparted on the Live CD will work just fine, I've done it countless times. Just open up gparted, right click on your NTFS partition, resize/move, enter new size, apply, voilà :)

---

### Post by ReaderRat on 2006-10-18
Thank you HymnToLife. I was not sure.

---

### Post by neobonzi on 2006-10-18
Wow! look at all the great responses! thanks buddies!

Well - I tried running Gparted in the first place but unfortunately it gives me the error that it "cant create enough disk space" every time i do it. That is why i defragged and ChkDsk'd and whatnot. I even tried using partitionmagic 8 but that program seems to be having just as much trouble as gparted:

I'm going to try defragging in safe mode right now to see if that might help and then run gparted from the live cd.

Does anyone else know of any other ways I can either get gparted to work or somehow resize my windows partition? ](*,)

---

### Post by neobonzi on 2006-10-18
Quick update:

So I tried restarting in safe mode and defragging. But im still not able to shrink my partition during the installation of ubuntu or with gpart.

1) When i run gpart and specify what i want done then click apply, the program simply runs for awhile (i looked at the details and its running through the motions) but after 30 seconds or so it simply stops, refreshes, and im back where I was. Weird?

2) When i try to use the installation to shrink my partition it says "failed to create enough space" and fails to do anything.

MAN windblows is stubborn :-k

---

### Post by Foudre on 2006-10-18
> **neobonzi said:**
> So I decided to install Ubuntu on my E1505 Dell Laptop because I just started college and I have to keep up with all the other nerdy comp sci major kids who have linux kernels for brains.

BUT...I have a problem.

I can't seem to resize my windows partition! I used the LIVE cd from ubuntu to try to install it but when i get to the part where I   'm supposed to adjust my partitions - i get the error message "Couldn't create a partition with enough space".

I've Defragged my computer twice, tried running the partition editor program thing (forget the name) from inside ubuntu ( which simple paused for a bit, said it was working, then went back to the screen it was at before. ).

And now im frustrated. Any advice to resizing my windows partition so i can install ubuntu on the leftover space?

Computer Specs:
E1505 1gig DDR Dual Channel ram
80 gig HD
Windows XP Home 
Ati X1400 Graphics card

Ahh, you seam to have the same issue i did. my computer is almost the same (DELL INSPIRON e1505) just different video card

ok i tried all the classic responses they suggested along time ago, it failed. so i did something rash

it seams that the dell utility partion protects itself... or makes itself a pain to get rid off. What i did, i wanted to do it without having to loose all my windows data (i backed some things up of course, but dell is cheap and doesn't include all the drivers for the e1505 on the disk they give you -- if you do this or something similiar i can get you the link to where the driver is at, i may still have it archived somewhere too)

sorry back to what i did, after backing stuff up, i rebooted to the windows media center dvd that came with the computer, after it did its long retarded copying files that its about to format over anyways (lol) i told it to redo some of the partitioning i deleted the dell utility partition, the main windows partition, and the dell restore partition. I created a new partion after that for windows 45 gig, and free space for linux of 26 gig (don't be fooled they say its an 80 gig hard drive buts its really only a little over 70)

after reinstalling windows and going thru the hassle of tracking down some drivers they neglected to include and some very slow slow download rates (fricken 50 meg video drivers at 5 k a seconds....., i gave up and had a freind download it and give it to me) 

then i installed ubuntu told it to make the swap partition and the root parition, and it was golden 15 minutes after ubuntu started installing and making partitions and installing grub, it was done yay.
 
Thats how i got it done, their may be a way to not loose data but it just didn't seem like the slef protecting utilty partiion was going to let me resize anything, after it was gone no problems

---

### Post by neobonzi on 2006-10-18
OY! this makes me wish i wouldve thought about linux when i formatted my computer before!

I'm at college right  now and don't have my flippin' dell disks so I was trying to avoid having to use those.

I've considered just going back and whiping out winblows and starting fresh but getting on my school network requires you to spend a billion hours downloading and installing their "anti-piracy/spyware/malcicious user/wardriver/etc" software on your windows machine before youre allowed to connect to the internet in the dorms. (Linux users, of course, dont need to install ANYTHING) So if i cant shrink windows without losing my info I cant install linux! SUCKS!

I looked on other threads and some other people ahve successfuly reduced their windows partitions on dell laptops - HOW DO YOU PEOPLE DO IT?! ](*,)

---

### Post by neobonzi on 2006-10-18
Ohhhhhmygosh.....

[SIZE="7"]IT WORKS!!!![/SIZE]

  So apparently all I needed to do was turn off my 'static pagefile' and defragment again. After that I started up the live cd and shrunk my partition + installed ubuntu NO PROBLEM!!!! I'm typing from my lovely ubuntu firefox desktop at the moment! Thanks for all your guys help!

---

### Post by Foudre on 2006-10-18
wish i knew about that back then, but now days it doesn't even matter, i did loose some of my artwork though, forgot to back taht up, but i saved my music. lol static pagefile huh, i'll have to remember that, i got a freind back home with the same problem, First year of college here too, but i isntalled my first linux awhile back, slackware (i got a nice text based interface lol) Now that i'm going to japan next year I like having linux because its alot easier to read and type in japanes then windows allows.

---

### Post by longrunner on 2006-11-05
I'm having the same problem on my compaq v5000, how do you turn off the pagefile?

---

### Post by hush on 2006-11-27
I've got a compaq v5000 too and I'm having the exact same problems..
Can't resize my windows partition :(

what is the static pagefile?
is that in linux or windows G

---

### Post by aprilcanadian on 2006-11-27
i was so sick of windows when i had this same issue trying to partition i said heck with it and completlty deleted XP in a mad fit of rage! Was very happy with Ubuntu alone after although I have a second comp now I run xp on as well to do the very few things i couldnt with ubunutu *very few*.

i am so happy with ubuntu and the educational games my kids just loves. My 5 year old has no problems finding her way around it at all.

---

### Post by neobonzi on 2007-01-02
Hey guys! It's been awhile since i posted this but I'm getting PM's and things from people wondering how I turned off the static page file.

Right Click on My Computer
Select Properties
Select Advanced Tab
Click Settings under Performance
Performance Options window pops up
Select Advanced
Select Change under Virtual Memory

Now just choose "System Managed Size" instead of custom size for your drive.

Hope this helps!

---

