---
title: "How do I save new/edited code?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Deros on 2007-07-08
Hi, I am following The Perfect Setup - Ubuntu 6.06 LTS Server (Dapper Drake)
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3)

and edited the file 

vi /etc/network/interfaces

to this:

# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static        
address 192.168.0.100        
netmask 255.255.255.0        
network 192.168.0.0        
broadcast 192.168.0.255        
gateway 192.168.0.1 

The next instruction is to:

Then restart your network: 

/etc/init.d/networking restart 

How do I save the edit and return to the command line?

Thanks,
Deros

---

### Post by ltk5 on 2007-07-08
Type <esc>:w<return>

more info can be found at:[INDENT][http://www.cs.colostate.edu/helpdocs/vi.html](http://www.cs.colostate.edu/helpdocs/vi.html)
[http://www.vmunix.com/~gabor/vi.html](http://www.vmunix.com/~gabor/vi.html)[/INDENT]

---

### Post by jimbob on 2007-07-08
In vi press ESC to make sure you are back in command mode.

Then at the bottom left where the colon (:) appears enter *[COLOR="Blue"]wq[/COLOR]*

This will write (save) and quit vi and you are back in terminal mode.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Deros on 2007-07-08
Thanks guys, that did the trick.  

I just got back from watching Shrek 3, what a bore I fell asleep which I don't ever do.  Last movie I fell asleep in was the Eddie Murphy stand up comedy movie Delirious.  

Anyway, thanks again,
Deros

---

