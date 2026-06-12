---
title: "libmtp doesn't exist"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2007-12-26
Can't get it...
I have screwed around with my repository settings to the point that they are prolly un-fixable now, but with everything I can find enabled, 'sudo aptitude install libmtp' and 'sudo apt-get install libmtp' do nothing. The file isn't in synaptic either. 


I use Dapper, because none of the newer versions allow my laptop to function.

---

### Post by wormser on 2007-12-26
You probably can fix the repositories.  Can you install anything?  I am on Gusty and the package was called libmtp6.  Try doing **apt-cache search libmtp**.  It might be name a little bit different.

---

### Post by Papa-san on 2007-12-26
There are no results when I do 'apt-cache search libmtp'

I can install. I installed gnomad2 ok. (It just doesn't work!)

---

### Post by Hospadar on 2007-12-26
as it turns out, it doesn't exist! at least it's not in the dapper repositories.
You could try: building it from source - [http://libmtp.sourceforge.net/](http://libmtp.sourceforge.net/)
or try downloading the feisty package (the .deb) and see if it will install
libmtp5 - [http://packages.ubuntu.com/feisty/libs/libmtp5](http://packages.ubuntu.com/feisty/libs/libmtp5)
libmtp-dev (for building things that need libmtp - _[http://packages.ubuntu.com/feisty/libdevel/libmtp-dev](http://packages.ubuntu.com/feisty/libdevel/libmtp-dev)_

---

### Post by Papa-san on 2007-12-26
I don't know how to do this.
Any idea where I should download and install these things to? (Including the dependencies.)

---

