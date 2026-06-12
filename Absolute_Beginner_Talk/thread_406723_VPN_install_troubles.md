---
title: "VPN install troubles"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by cosmo18 on 2007-04-11
I am trying to get the software for my job working in kubuntu, if I can get this stuff working I can kiss windoze goodby. anyways when I try to install the VPN software I get this error ```
What is the location of your linux kernel source? [/usr/src/linux]
/

Determining distribution... detected Linux--unknown.
Unpacking (17754+1129770+20=1147544)...
1129790
Checksumming...
0
0
Extracting...
Installing...
strip: /usr/sbin/net6vpnd: File format not recognized
install: strip failed
install: cannot stat `/tmp/.net6/net6vpnd..init': No such file or directory
install: cannot stat `/tmp/.net6/net6vpn': No such file or directory
Installing ip_queue kernel module...
gcc: /tmp/.net6/ip_queue.c: No such file or directory
gcc: no input files
Adding net6vpnd to default runlevel...
Starting daemon
./citrixvpn-linux-2.4-i386.sh: 416: /etc/init.d/net6vpnd: not found
Cleaning up...
Done.

```
any clues how to fix this?

---

### Post by niais77 on 2007-04-11
are you trying to install a vpn daemon or a vpn client?
I would assume you're just trying to connect to your workplace VPN, yes?

---

### Post by dstew on 2007-04-11
It might be installed. None of the error messages looks fatal. Have you tried **net6vpn** on the command line to see if the client application works?

EDIT: Have you compiled other programs successfully before? That is, you have your linux-headers and build-essential packages installed, right?

---

### Post by cosmo18 on 2007-04-11
I assume it's a VPN client, just following the directions on the page that my job provided, I'm still fairly new to linux and yes it is for connecting to my workplace VPN, as far as whether I have  linux-headers and build-essential packages installed I will check after work when I can boot back into Kubuntu

EDIT: I checked and yes I have both of those installed

---

### Post by cosmo18 on 2007-04-12
this is the link to the download and the instructions I am trying to follow [https://216.241.173.165/full_linux_instructions.html](https://216.241.173.165/full_linux_instructions.html) 
If I can get this working then all the other software I need is either web based or has a linux version

---

### Post by dstew on 2007-04-12
What happens when you run the client? That is, what happens when you enter **net6vpn** on the command line?

EDIT: Here's another thought: Are you sure your linux source files are in /? I think in Ubuntu they are in /usr/src. Maybe that is the problem.

---

### Post by jconides on 2007-04-17
I tried installing and go the same error message. I then tried installing and pointing the installer to /usr/src/linux-headers-2.6.15-28-686 and got different errors:

Determining distribution... detected Linux--unknown.
Unpacking (17754+1108748+25=1126527)...
1108773
Checksumming...
0
0
Extracting...
Installing...
install: cannot stat `/tmp/.net6/net6vpnd..init': No such file or directory
Installing ip_queue kernel module...
In file included from /usr/src/linux-headers-2.6.15-28-686/include/asm/system.h:5,
                 from /usr/src/linux-headers-2.6.15-28-686/include/asm/processor.h:18,
                 from /usr/src/linux-headers-2.6.15-28-686/include/asm/thread_info.h:17,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/thread_info.h:21,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/preempt.h:10,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/spinlock.h:50,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/capability.h:45,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/sched.h:7,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/module.h:10,
                 from /tmp/.net6/ip_queue.c:15:
/usr/src/linux-headers-2.6.15-28-686/include/linux/kernel.h:10:20: error: stdarg.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.15-28-686/include/asm/system.h:5,
                 from /usr/src/linux-headers-2.6.15-28-686/include/asm/processor.h:18,
                 from /usr/src/linux-headers-2.6.15-28-686/include/asm/thread_info.h:17,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/thread_info.h:21,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/preempt.h:10,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/spinlock.h:50,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/capability.h:45,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/sched.h:7,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/module.h:10,
                 from /tmp/.net6/ip_queue.c:15:
/usr/src/linux-headers-2.6.15-28-686/include/linux/kernel.h:102: error: syntax error before ‘va_list’
/usr/src/linux-headers-2.6.15-28-686/include/linux/kernel.h:103: warning: function declaration isn’t a prototype
/usr/src/linux-headers-2.6.15-28-686/include/linux/kernel.h:106: error: syntax error before ‘va_list’
/usr/src/linux-headers-2.6.15-28-686/include/linux/kernel.h:107: warning: function declaration isn’t a prototype
/usr/src/linux-headers-2.6.15-28-686/include/linux/kernel.h:110: error: syntax error before ‘va_list’
/usr/src/linux-headers-2.6.15-28-686/include/linux/kernel.h:111: warning: function declaration isn’t a prototype
/usr/src/linux-headers-2.6.15-28-686/include/linux/kernel.h:115: error: syntax error before ‘va_list’
/usr/src/linux-headers-2.6.15-28-686/include/linux/kernel.h:116: warning: function declaration isn’t a prototype
/usr/src/linux-headers-2.6.15-28-686/include/linux/kernel.h:127: error: syntax error before ‘va_list’
/usr/src/linux-headers-2.6.15-28-686/include/linux/kernel.h:128: warning: function declaration isn’t a prototype
In file included from /usr/src/linux-headers-2.6.15-28-686/include/asm/smp.h:18,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/smp.h:19,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/sched.h:26,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/module.h:10,
                 from /tmp/.net6/ip_queue.c:15:
/usr/src/linux-headers-2.6.15-28-686/include/asm/mpspec.h:6:25: error: mach_mpspec.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.15-28-686/include/asm/smp.h:18,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/smp.h:19,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/sched.h:26,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/module.h:10,
                 from /tmp/.net6/ip_queue.c:15:
/usr/src/linux-headers-2.6.15-28-686/include/asm/mpspec.h:8: error: ‘MAX_MP_BUSSES’ undeclared here (not in a function)
/usr/src/linux-headers-2.6.15-28-686/include/asm/mpspec.h:23: error: ‘MAX_IRQ_SOURCES’ undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.15-28-686/include/linux/smp.h:19,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/sched.h:26,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/module.h:10,
                 from /tmp/.net6/ip_queue.c:15:
/usr/src/linux-headers-2.6.15-28-686/include/asm/smp.h:77:26: error: mach_apicdef.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.15-28-686/include/linux/smp.h:19,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/sched.h:26,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/module.h:10,
                 from /tmp/.net6/ip_queue.c:15:
/usr/src/linux-headers-2.6.15-28-686/include/asm/smp.h: In function ‘hard_smp_processor_id’:
/usr/src/linux-headers-2.6.15-28-686/include/asm/smp.h:81: warning: implicit declaration of function ‘GET_APIC_ID’
In file included from /usr/src/linux-headers-2.6.15-28-686/include/linux/irq.h:22,
                 from /usr/src/linux-headers-2.6.15-28-686/include/asm/hardirq.h:6,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/hardirq.h:7,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/interrupt.h:11,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/rcuref.h:36,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/fs.h:12,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/mm.h:15,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/skbuff.h:26,
                 from /tmp/.net6/ip_queue.c:16:
/usr/src/linux-headers-2.6.15-28-686/include/asm/irq.h:16:25: error: irq_vectors.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.15-28-686/include/asm/hardirq.h:6,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/hardirq.h:7,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/interrupt.h:11,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/rcuref.h:36,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/fs.h:12,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/mm.h:15,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/skbuff.h:26,
                 from /tmp/.net6/ip_queue.c:16:
/usr/src/linux-headers-2.6.15-28-686/include/linux/irq.h: At top level:
/usr/src/linux-headers-2.6.15-28-686/include/linux/irq.h:85: error: ‘NR_IRQS’ undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.15-28-686/include/linux/irq.h:94,
                 from /usr/src/linux-headers-2.6.15-28-686/include/asm/hardirq.h:6,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/hardirq.h:7,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/interrupt.h:11,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/rcuref.h:36,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/fs.h:12,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/mm.h:15,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/skbuff.h:26,
                 from /tmp/.net6/ip_queue.c:16:
/usr/src/linux-headers-2.6.15-28-686/include/asm/hw_irq.h:30: error: ‘NR_IRQ_VECTORS’ undeclared here (not in a function)
In file included from /tmp/.net6/ip_queue.c:16:
/usr/src/linux-headers-2.6.15-28-686/include/linux/skbuff.h: In function ‘skb_add_data’:
/usr/src/linux-headers-2.6.15-28-686/include/linux/skbuff.h:1128: warning: pointer targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
In file included from /usr/src/linux-headers-2.6.15-28-686/include/net/request_sock.h:22,
                 from /usr/src/linux-headers-2.6.15-28-686/include/linux/ip.h:84,
                 from /tmp/.net6/ip_queue.c:18:
/usr/src/linux-headers-2.6.15-28-686/include/net/sock.h: In function ‘skb_copy_to_page’:
/usr/src/linux-headers-2.6.15-28-686/include/net/sock.h:1064: warning: pointer targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
/tmp/.net6/ip_queue.c: At top level:
/tmp/.net6/ip_queue.c:118: error: syntax error before ‘outfn’
/tmp/.net6/ip_queue.c:121: warning: function declaration isn’t a prototype
/tmp/.net6/ip_queue.c: In function ‘ipq_create_queue’:
/tmp/.net6/ip_queue.c:125: error: ‘errp’ undeclared (first use in this function)
/tmp/.net6/ip_queue.c:125: error: (Each undeclared identifier is reported only once
/tmp/.net6/ip_queue.c:125: error: for each function it appears in.)
/tmp/.net6/ip_queue.c:135: error: ‘send_cb’ undeclared (first use in this function)
/tmp/.net6/ip_queue.c:137: error: ‘sysctl_qmax’ undeclared (first use in this function)
/tmp/.net6/ip_queue.c:142: error: ‘outfn’ undeclared (first use in this function)
/tmp/.net6/ip_queue.c:142: error: too many arguments to function ‘nf_register_queue_handler’
/tmp/.net6/ip_queue.c: In function ‘ipq_mangle_ipv4’:
/tmp/.net6/ip_queue.c:253: error: ‘struct sk_buff’ has no member named ‘nfcache’
/tmp/.net6/ip_queue.c:253: error: ‘NFC_ALTERED’ undeclared (first use in this function)
/tmp/.net6/ip_queue.c: In function ‘netlink_build_message’:
/tmp/.net6/ip_queue.c:428: error: ‘struct sk_buff’ has no member named ‘stamp’
/tmp/.net6/ip_queue.c:429: error: ‘struct sk_buff’ has no member named ‘stamp’
/tmp/.net6/ip_queue.c:447: error: ‘struct netlink_skb_parms’ has no member named ‘dst_groups’
/tmp/.net6/ip_queue.c: In function ‘netlink_receive_user_sk’:
/tmp/.net6/ip_queue.c:521: error: ‘struct sock’ has no member named ‘receive_queue’
/tmp/.net6/ip_queue.c:526: error: ‘struct sock’ has no member named ‘receive_queue’
/tmp/.net6/ip_queue.c: In function ‘init’:
/tmp/.net6/ip_queue.c:627: warning: passing argument 2 of ‘netlink_kernel_create’ makes integer from pointer without a cast
/tmp/.net6/ip_queue.c:627: error: too few arguments to function ‘netlink_kernel_create’
/tmp/.net6/ip_queue.c:638: error: ‘struct sock’ has no member named ‘socket’
/tmp/.net6/ip_queue.c:645: error: ‘struct sock’ has no member named ‘socket’
/tmp/.net6/ip_queue.c: In function ‘fini’:
/tmp/.net6/ip_queue.c:659: error: ‘struct sock’ has no member named ‘socket’
Adding net6vpnd to default runlevel...
Starting daemon
/home/jconides/Desktop/citrixvpn-linux-2.4-i386.sh: line 416: /etc/init.d/net6vpnd: No such file or directory
Cleaning up...
Done.


When I tried to run net6vpn, I got:

jconides@JC-NC8000:~$ net6vpn
net6vpn: net: socket: socket hung up.
net6vpn: failed to connect to daemon. [Operation now in progress]
net6vpn: failed to do network io.
net6vpn: failed to get connection id.
jconides@JC-NC8000:~$ sudo net6vpn
net6vpn: net: socket: socket hung up.
net6vpn: failed to connect to daemon. [Operation now in progress]
net6vpn: failed to do network io.
net6vpn: failed to get connection id.


Any body have any ideas what these errors mean?

---

### Post by michaelwayneharwood on 2007-04-18
The VPN install script does not correctly install an init script into /etc/init.d - the net6vpn executable requires the net6vpnd daemon to be running as it handles all of the backend routing, so you either need to run /usr/sbin/net6vpnd manually or create your own init script.  The errors you are seeing are telling you that the net6vpn client is not able to talk to the net6vpnd process.

---

### Post by jconides on 2007-04-18
Thanks,

I tried launching net6vpnd manually as root, and here's the output:

net6vpnd: net: socket: initializing.
net6vpnd: ip: initializing.
net6vpnd: ip: tcp: starting.
net6vpnd: ip: starting.
net6vpnd: ip: filter: starting.
net6vpnd: ip: filter: failed to set mode. [Failed to send netlink message]
net6vpnd: ip: filter: failed to create handle.
net6vpnd: ip: failed to start ip filter.
net6vpnd: ip: filter: stopping.
net6vpnd: failed to start ip.
net6vpnd: client listener: stopping.
1net6vpnd: event listener: stopping.
net6vpnd: ip: stopping.
net6vpnd: ip: filter: stopping.
net6vpnd: ip: udp: stopping.
net6vpnd: ip: tcp: stopping.
net6vpnd: ip: icmp: stopping icmp tunnel.
net6vpnd: ip: icmp: icmp tunnel stopped.
net6vpnd: ip: shutting down.
net6vpnd: net: socket: shut down.
net6vpnd: stopped.


It did ask if I had iptables installed, which I do, not sure if this is the issue.

---

### Post by raves71 on 2007-07-12
I've got the same Issue as jconides - please help!

---

