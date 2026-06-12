---
title: "Problems updating to Edgy amd64! Update manager errors"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Enginirical on 2007-06-08
Hi

Ive been having major difficulties updating from Dapper to Edgy.

first i got API not stable future warning message when I type 
gksu "update-manager -c" in the terminal. installing python changed nothing!

Then I typed this in the terminal: sudo apt-get update
                                               sudo apt-get dist-upgrade
and then nothing happened!

Now I cant open Update manager and theres an error message to do with sorces list I did try to add [http://us.archive.ubuntu.com.ubuntu/](http://us.archive.ubuntu.com.ubuntu/) but couldnt find the right form of typing it:
    
deb [http://us.archive.ubuntu.com.ubuntu/](http://us.archive.ubuntu.com.ubuntu/) edgy ??

I'd realy appreciate some one to point me in the right direction on fixing this!

Thanks

Her is my sources list:


# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)

---

### Post by Enginirical on 2007-06-08
ok I got rid of the last 3 lines, and it fine now.

But I still dont know what to write to get the edgy upgrade!?

And Im still getting API not stable future warning message with gksu "update-manager -c" :(

---

