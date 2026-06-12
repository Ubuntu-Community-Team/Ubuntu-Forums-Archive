---
title: "BUG: unable to handle kernel paging request at virtual address"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by marx2k on 2007-01-30
I dont know exactly what has changed on my system but I am linked to a computer via a router via NFS... I can get files from that computer fine, but if I try to copy files to that computer, NFS totally freezes up, Nautilus freezes up on my system and I eventually get this:

```

[17180393.008000] BUG: unable to handle kernel paging request at virtual address 00e6e7e6
[17180393.008000]  printing eip:
[17180393.008000] c026cca4
[17180393.008000] *pde = 00000000
[17180393.008000] Oops: 0000 [#1]
[17180393.008000] SMP 
[17180393.008000] Modules linked in: vmnet vmmon binfmt_misc nfnetlink_queue nfsd exportfs xt_NFQUEUE iptable_nat ip_nat_irc ip_nat_ftp xt_limit xt_tcpudp iptable_mangle ipt_LOG ipt_MASQUERADE ip_nat ipt_TOS ipt_REJECT ip_conntrack_irc ip_conntrack_ftp xt_state ip_conntrack nfnetlink iptable_filter ip_tables x_tables fglrx nfs lockd sunrpc cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative hotkey af_packet video sbs pcc_acpi i2c_ec dev_acpi container button asus_acpi ac ati_agp sbp2 lp tsdev sg 3c59x mii floppy serio_raw evdev snd_intel8x0 pcspkr snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss psmouse parport_pc parport snd_pcm snd_timer snd soundcore snd_page_alloc shpchp pci_hotplug i2c_nforce2 i2c_core nvidia_agp agpgart ext3 jbd ehci_hcd ohci_hcd usbcore ohci1394 ieee1394 ide_generic sd_mod sata_sil ide_cd cdrom ide_disk generic amd74xx sata_nv libata scsi_mod thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[17180393.008000] CPU:    0
[17180393.008000] EIP:    0060:[<c026cca4>]    Tainted: P      VLI
[17180393.008000] EFLAGS: 00010212   (2.6.17-10-generic #2) 
[17180393.008000] EIP is at pskb_expand_head+0xa4/0x120
[17180393.008000] eax: 00000100   ebx: e90db144   ecx: 00000003   edx: 00e6e7e6
[17180393.008000] esi: e949aa24   edi: e9ea4e24   ebp: e9ea4d80   esp: f7cbdc94
[17180393.008000] ds: 007b   es: 007b   ss: 0068
[17180393.008000] Process rpciod/0 (pid: 4088, threadinfo=f7cbc000 task=dfcd7050)
[17180393.008000] Stack: e9ea4c00 e9ea4c00 e90db144 e949a958 e949a96c 00000003 c0270f00 00000020 
[17180393.008000]        00000003 e90db144 c0494a58 f8d0f512 f6123dbc 00000070 00000000 00000000 
[17180393.008000]        f7cbdd78 00000000 00000003 6401a8c0 00000003 f7cbdd78 c0494a58 80000000 
[17180393.008000] Call Trace:
[17180393.008000]  <c0270f00> skb_checksum_help+0xb0/0xe0  <f8d0f512> ip_nat_fn+0x182/0x1e0 [iptable_nat]
[17180393.008000]  <f8d0f856> ip_nat_local_fn+0x66/0xe0 [iptable_nat]  <c02928d0> dst_output+0x0/0x10
[17180393.008000]  <c0288f23> nf_iterate+0x63/0x90  <c02928d0> dst_output+0x0/0x10
[17180393.008000]  <c0289079> nf_hook_slow+0x59/0xe0  <c02928d0> dst_output+0x0/0x10
[17180393.008000]  <c0294ede> ip_queue_xmit+0x2ae/0x450  <c02928d0> dst_output+0x0/0x10
[17180393.008000]  <c02b6f57> inet_sendmsg+0x37/0x70  <c02663c6> sock_sendmsg+0x116/0x130
[17180393.008000]  <c02a4b1b> tcp_transmit_skb+0x36b/0x7a0  <c0136180> autoremove_wake_function+0x0/0x50
[17180393.008000]  <c02a43cd> tcp_snd_test+0x1d/0x110  <c02a6d55> tcp_push_one+0xa5/0x130
[17180393.008000]  <c029a8cc> tcp_sendpage+0x60c/0x630  <f8ce8e59> xs_tcp_send_request+0x169/0x400 [sunrpc]
[17180393.008000]  <c029a2c0> tcp_sendpage+0x0/0x630  <f8d6c320> nfs3_xdr_writeargs+0x0/0xa0 [nfs]
[17180393.008000]  <f8ce7b3e> xprt_transmit+0x4e/0x220 [sunrpc]  <f8d6c320> nfs3_xdr_writeargs+0x0/0xa0 [nfs]
[17180393.008000]  <f8cec1dc> rpcauth_wrap_req+0x6c/0xa0 [sunrpc]  <f8cec2a9> rpcauth_marshcred+0x29/0x70 [sunrpc]
[17180393.008000]  <f8d6c320> nfs3_xdr_writeargs+0x0/0xa0 [nfs]  <f8ce6abe> call_transmit+0x15e/0x230 [sunrpc]
[17180393.008000]  <f8ceb737> __rpc_execute+0x67/0x1f0 [sunrpc]  <c0132702> run_workqueue+0x72/0xf0
[17180393.008000]  <f8ceb8c0> rpc_async_schedule+0x0/0x10 [sunrpc]  <c01332e7> worker_thread+0x117/0x140
[17180393.008000]  <c011bde0> default_wake_function+0x0/0x10  <c01331d0> worker_thread+0x0/0x140
[17180393.008000]  <c0135f8b> kthread+0xab/0xe0  <c0135ee0> kthread+0x0/0xe0
[17180393.008000]  <c0101005> kernel_thread_helper+0x5/0x10 
[17180393.008000] Code: 74 02 f3 a4 03 2c 24 b9 29 00 00 00 8b b3 a0 00 00 00 89 ef f3 a5 8b 93 a0 00 00 00 66 83 7a 04 00 74 24 31 c9 89 f6 8b 54 ca 14 <8b> 02 f6 c4 40 75 6f 90 ff 42 04 8b 93 a0 00 00 00 83 c1 01 0f 
[17180393.008000] EIP: [<c026cca4>] pskb_expand_head+0xa4/0x120 SS:ESP 0068:f7cbdc94
[17180393.008000]  

```

The only thing I can think of that Ive done is installed WINE lately. Thats about it. In order to completely recover, I need to do a reboot of Linux.  Otherwise Nautilus is sluggish.

Both systems are Edgy i386's

---

### Post by marx2k on 2007-01-30
Im thinking this might have something to do with it also... I dont know what this is (Im guessing this has to do with my VMWare install..

```

[17179614.032000] /dev/vmmon[5156]: Module vmmon: registered with major=10 minor=165
[17179614.032000] /dev/vmmon[5156]: Module vmmon: initialized
[17179614.824000] /dev/vmnet: open called by PID 5182 (vmnet-bridge)
[17179614.824000] /dev/vmnet: hub 0 does not exist, allocating memory.
[17179614.824000] /dev/vmnet: port on hub 0 successfully opened
[17179614.824000] bridge-eth1: enabling the bridge
[17179614.824000] bridge-eth1: up
[17179614.824000] bridge-eth1: already up
[17179614.824000] bridge-eth1: attached
[17179614.940000] /dev/vmnet: open called by PID 5196 (vmnet-natd)
[17179614.940000] /dev/vmnet: hub 8 does not exist, allocating memory.
[17179614.940000] /dev/vmnet: port on hub 8 successfully opened
[17179625.036000] /dev/vmnet: open called by PID 5390 (vmnet-netifup)
[17179625.036000] /dev/vmnet: hub 1 does not exist, allocating memory.
[17179625.036000] /dev/vmnet: port on hub 1 successfully opened
[17179625.048000] /dev/vmnet: open called by PID 5391 (vmnet-netifup)
[17179625.048000] /dev/vmnet: port on hub 8 successfully opened
[17179625.304000] /dev/vmnet: open called by PID 5416 (vmnet-dhcpd)
[17179625.304000] /dev/vmnet: port on hub 8 successfully opened
[17179625.524000] /dev/vmnet: open called by PID 5417 (vmnet-dhcpd)
[17179625.524000] /dev/vmnet: port on hub 1 successfully opened

```

But I dont want this running when VMWare is not running...

I also get this in ifconfig...
```

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.240.1  Bcast:172.16.240.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.85.1  Bcast:172.16.85.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

It just seems like this has messed my net config up because previously I was able to SSH to 'livingroombuntu' to get to 192.168.1.101 -- now I have to give the explicit IP address... 

What can one do to begin fixing these issues? The most pressing at the moment is the NFS issue and not being able to copy a file over to the other computer that's attached.

---

### Post by marx2k on 2007-01-30
After trying to copy a file to the remote NFS server, I get this...

[17206412.460000] nfs: server 192.168.1.101 not responding, still trying

(thats the remote server)

I try to hit cancel on the transfer but Nautilus doesn't respond for a long time, then it allows me to Force Quit, but that crashes Nautilus and I have to basically reboot in order to get my computer to work normally again.

And then 5 minutes later, I get a system beep and it throws this at me in terminal:
```

[17206924.164000] BUG: unable to handle kernel paging request at virtual address ffeeeeee
[17206924.164000]  printing eip:
[17206924.164000] c026cca4
[17206924.164000] *pde = 00004067
[17206924.164000] Oops: 0000 [#1]
[17206924.164000] SMP 
[17206924.164000] Modules linked in: ppdev vmnet vmmon binfmt_misc nfnetlink_queue nfsd exportfs xt_NFQUEUE iptable_nat ip_nat_irc ip_nat_ftp xt_limit xt_tcpudp iptable_mangle ipt_LOG ipt_MASQUERADE ip_nat ipt_TOS ipt_REJECT ip_conntrack_irc ip_conntrack_ftp xt_state ip_conntrack nfnetlink iptable_filter ip_tables x_tables fglrx cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative hotkey nfs lockd sunrpc af_packet video sbs pcc_acpi i2c_ec dev_acpi container button asus_acpi ac ati_agp sbp2 lp sg snd_intel8x0 snd_ac97_codec snd_ac97_bus evdev snd_pcm_oss snd_mixer_oss tsdev serio_raw parport_pc parport psmouse snd_pcm snd_timer snd soundcore pcspkr 3c59x snd_page_alloc floppy mii shpchp pci_hotplug i2c_nforce2 i2c_core nvidia_agp agpgart ext3 jbd ehci_hcd ohci1394 ieee1394 ohci_hcd usbcore ide_generic sd_mod sata_sil ide_cd cdrom ide_disk generic amd74xx sata_nv libata scsi_mod thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[17206924.164000] CPU:    0
[17206924.164000] EIP:    0060:[<c026cca4>]    Tainted: P      VLI
[17206924.164000] EFLAGS: 00010216   (2.6.17-10-generic #2) 
[17206924.164000] EIP is at pskb_expand_head+0xa4/0x120
[17206924.164000] eax: 00006700   ebx: de715124   ecx: 00000004   edx: ffeeeeee
[17206924.164000] esi: db02de24   edi: d8eef624   ebp: d8eef580   esp: f7e83c94
[17206924.164000] ds: 007b   es: 007b   ss: 0068
[17206924.164000] Process rpciod/0 (pid: 3699, threadinfo=f7e82000 task=dfd3b580)
[17206924.164000] Stack: d8eef400 d8eef400 de715124 db02dd58 db02dd6c 00000003 c0270f00 00000020 
[17206924.164000]        00000003 de715124 c0494a58 f8d31512 f6ceddbc 00000070 00000000 00000000 
[17206924.164000]        f7e83d78 00000000 00000003 6401a8c0 00000003 f7e83d78 c0494a58 80000000 
[17206924.164000] Call Trace:
[17206924.164000]  <c0270f00> skb_checksum_help+0xb0/0xe0  <f8d31512> ip_nat_fn+0x182/0x1e0 [iptable_nat]
[17206924.164000]  <f8d31856> ip_nat_local_fn+0x66/0xe0 [iptable_nat]  <c02928d0> dst_output+0x0/0x10
[17206924.164000]  <c0288f23> nf_iterate+0x63/0x90  <c02928d0> dst_output+0x0/0x10
[17206924.164000]  <c0289079> nf_hook_slow+0x59/0xe0  <c02928d0> dst_output+0x0/0x10
[17206924.164000]  <c0294ede> ip_queue_xmit+0x2ae/0x450  <c02928d0> dst_output+0x0/0x10
[17206924.164000]  <c02b6f57> inet_sendmsg+0x37/0x70  <c02663c6> sock_sendmsg+0x116/0x130
[17206924.164000]  <c011b8e7> activate_task+0x67/0xb0  <c02a4b1b> tcp_transmit_skb+0x36b/0x7a0
[17206924.164000]  <c0136180> autoremove_wake_function+0x0/0x50  <c02a43cd> tcp_snd_test+0x1d/0x110
[17206924.164000]  <c02a6d55> tcp_push_one+0xa5/0x130  <c029a8cc> tcp_sendpage+0x60c/0x630
[17206924.164000]  <f8ce2e59> xs_tcp_send_request+0x169/0x400 [sunrpc]  <c029a2c0> tcp_sendpage+0x0/0x630
[17206924.164000]  <f8d66320> nfs3_xdr_writeargs+0x0/0xa0 [nfs]  <f8ce1b3e> xprt_transmit+0x4e/0x220 [sunrpc]
[17206924.164000]  <f8d66320> nfs3_xdr_writeargs+0x0/0xa0 [nfs]  <f8ce61dc> rpcauth_wrap_req+0x6c/0xa0 [sunrpc]
[17206924.164000]  <f8ce62a9> rpcauth_marshcred+0x29/0x70 [sunrpc]  <f8d66320> nfs3_xdr_writeargs+0x0/0xa0 [nfs]
[17206924.164000]  <f8ce0abe> call_transmit+0x15e/0x230 [sunrpc]  <f8ce5737> __rpc_execute+0x67/0x1f0 [sunrpc]
[17206924.164000]  <c0132702> run_workqueue+0x72/0xf0  <f8ce58c0> rpc_async_schedule+0x0/0x10 [sunrpc]
[17206924.164000]  <c01332e7> worker_thread+0x117/0x140  <c011bde0> default_wake_function+0x0/0x10
[17206924.164000]  <c01331d0> worker_thread+0x0/0x140  <c0135f8b> kthread+0xab/0xe0
[17206924.164000]  <c0135ee0> kthread+0x0/0xe0  <c0101005> kernel_thread_helper+0x5/0x10
[17206924.164000] Code: 74 02 f3 a4 03 2c 24 b9 29 00 00 00 8b b3 a0 00 00 00 89 ef f3 a5 8b 93 a0 00 00 00 66 83 7a 04 00 74 24 31 c9 89 f6 8b 54 ca 14 <8b> 02 f6 c4 40 75 6f 90 ff 42 04 8b 93 a0 00 00 00 83 c1 01 0f 
[17206924.164000] EIP: [<c026cca4>] pskb_expand_head+0xa4/0x120 SS:ESP 0068:f7e83c94
[17206924.164000]  

```

---

### Post by marx2k on 2007-01-30
Since Nautilus crashes out on me completely, I try to re-start gnome..

THen I try to 'sudo umount -a'

And it works except for..
umount: /home/marx2k/Desktop/LivingroomBuntu/Scratch: device is busy

Thats the remote NFS server I was trying to copy to.  So I try 'sudo umount -f  /home/marx2k/Desktop/LivingroomBuntu/Scratch' 

And I get
umount2: Device or resource busy
umount: /home/marx2k/Desktop/LivingroomBuntu/Scratch: device is busy
umount2: Device or resource busy
umount: /home/marx2k/Desktop/LivingroomBuntu/Scratch: device is busy


In the remote machine's dmesg, I get these lines...
[17179620.848000] RPC: bad TCP reclen 0x0101080a (non-terminal)
[17181678.060000] RPC: bad TCP reclen 0x0101080a (non-terminal)
[17209863.624000] RPC: bad TCP reclen 0x0101080a (non-terminal)

And when I try to restart NFS on the rmeote machine, I still cant unmount the problem mount on the local machine.

This is how the NFS mounts for the remote machine look in my fstab...
```

192.168.1.101:/media/hdb4/Music /home/marx2k/Desktop/LivingroomBuntu/Music/Collection1 nfs rw,rsize=32768,wsize=32768,hard,intr,nfsvers=3,tcp,noatime,nodev,async,lock 
192.168.1.101:/media/hdd3/Music /home/marx2k/Desktop/LivingroomBuntu/Music/Collection2 nfs rw,rsize=32768,wsize=32768,hard,intr,nfsvers=3,tcp,noatime,nodev,async,lock
192.168.1.101:/media/hdf2/Music /home/marx2k/Desktop/LivingroomBuntu/Music/Collection3 nfs rw,rsize=32768,wsize=32768,hard,intr,nfsvers=3,tcp,noatime,nodev,async,lock
192.168.1.101:/media/hde3/Music /home/marx2k/Desktop/LivingroomBuntu/Music/Collection4 nfs rw,rsize=32768,wsize=32768,hard,intr,nfsvers=3,tcp,noatime,nodev,async,lock
192.168.1.101:/media/hdf3/DOCS  /home/marx2k/Desktop/LivingroomBuntu/Documents nfs rw,rsize=32768,wsize=32768,hard,intr,nfsvers=3,tcp,noatime,nodev,async,lock
192.168.1.101:/media/hde2/Shared  /home/marx2k/Desktop/LivingroomBuntu/Scratch nfs rw,rsize=32768,wsize=32768,hard,intr,nfsvers=3,tcp,noatime,nodev,async,lock

```

---

### Post by marx2k on 2007-01-30
Also seeing this error in /var/log/debug -- not sure if it's related but it seems to happen around that time:
```

Jan 30 10:48:33 Commodore-64 kernel: [17206999.312000] mtrr: no MTRR for d0800000,100000 found
Jan 30 10:48:33 Commodore-64 kernel: [17206999.312000] mtrr: no MTRR for d0900000,40000 found
Jan 30 10:48:33 Commodore-64 kernel: [17206999.312000] mtrr: no MTRR for d0940000,10000 found
Jan 30 10:48:33 Commodore-64 kernel: [17206999.312000] mtrr: no MTRR for d0950000,4000 found

```

---

### Post by marx2k on 2007-01-30
Well... I think I made some headway... still testing to see if it's going to work for good, but this is what I changed my fstab to...

```

192.168.1.101:/media/hdb4/Music /home/marx2k/Desktop/LivingroomBuntu/Music/Collection1 nfs rw,rsize=8192,wsize=8192,soft,nodev,async,lock 
192.168.1.101:/media/hdd3/Music /home/marx2k/Desktop/LivingroomBuntu/Music/Collection2 nfs rw,rsize=8192,wsize=8192,soft,nodev,async,lock
192.168.1.101:/media/hdf2/Music /home/marx2k/Desktop/LivingroomBuntu/Music/Collection3 nfs rw,rsize=8192,wsize=8192,soft,nodev,async,lock
192.168.1.101:/media/hde3/Music /home/marx2k/Desktop/LivingroomBuntu/Music/Collection4 nfs rw,rsize=8192,wsize=8192,soft,nodev,async,lock
192.168.1.101:/media/hdf3/DOCS  /home/marx2k/Desktop/LivingroomBuntu/Documents nfs rw,rsize=8192,wsize=8192,soft,nodev,async,lock
192.168.1.101:/media/hde2/Shared  /home/marx2k/Desktop/LivingroomBuntu/Scratch nfs rw,rsize=8192,wsize=8192,soft,nodev,async,lock

```

And it seems to have fixed it in that I can now transfer files to the drive with no timeouts, etc

---

### Post by marx2k on 2007-01-30
Scratch that... it totally didn't fix it... Im still getting the timeouts and Nautilus freezing due to this issue...

I will continue to try and figure out the problem

---

### Post by marx2k on 2007-01-30
Okay I *seem* to have gotten a little more headway here. After rebooting and before doing any work on copying to/from my remote NFS, I stopped all vmware services that started on boot.

'sudo /etc/init.d/vmware stop'

And so far everything seems to be ok.

The next thing I want to do is see how to stop those services from starting on boot either through configuring VMWare or editing the rc-startup scheme... but I am clueless how to do that :(

---

### Post by Brunellus on 2007-01-31
this is the wrong place to report bugs.  Devs don't read the forums (generally), much less Absolute beginners.

If you would like to report a bug, please follow the directions in this post:

[http://www.ubuntuforums.org/showthread.php?t=284595](http://www.ubuntuforums.org/showthread.php?t=284595)

---

