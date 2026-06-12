---
title: "weird errors in command line"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-10-16
```
sudo apt-get install audacity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Segmentation fault
glasgowm@glasgowm-desktop:~$ 
Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] Oops: 0000 [#19]

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] SMP 

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] CPU:    0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] EIP is at find_get_page+0x26/0x50

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] eax: 74756220   ebx: 000b6db2   ecx: 74756220   edx: 00000000

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] esi: c147c554   edi: 00000000   ebp: c147c440   esp: ce6c9ad0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] Process apt-get (pid: 24112, threadinfo=ce6c8000 task=c06c4030)

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] Stack: 00000000 000b6db2 c016c773 ef5cef5c 14e94300 003d77b4 ef5cef5c ce6c8000 

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]        c147c4ac c147c554 00568006 c147c554 00000000 00000008 c14063e0 c147c440 

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]        c016cb7f 000b6db2 00000000 00000000 00000000 ce6c8000 c147c4ac c147c554 

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] Call Trace:

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c016c773> __find_get_block_slow+0x53/0x170  <c016cb7f> __find_get_block+0x9f/0x1a0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c016cca3> __getblk+0x23/0x2e0  <c016ccac> __getblk+0x2c/0x2e0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c016e950> __bread+0x10/0xa0  <e09045bc> ext3_get_branch+0x8c/0x100 [ext3]

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <e0904812> ext3_get_blocks_handle+0xa2/0xb20 [ext3]  <c0152c56> __do_page_cache_readahead+0xd6/0x270

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c014ba30> find_get_page+0x20/0x50  <c0182b58> __d_lookup+0x88/0x110

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c0182b58> __d_lookup+0x88/0x110  <c014ba30> find_get_page+0x20/0x50

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c016c7a9> __find_get_block_slow+0x89/0x170  <c014ba30> find_get_page+0x20/0x50

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c015390f> activate_page+0x8f/0xa0  <c0153a1d> mark_page_accessed+0x2d/0x40

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <e0905633> ext3_get_block+0x83/0x100 [ext3]  <c018f784> do_mpage_readpage+0x204/0x710

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <e08ef2df> __journal_file_buffer+0xbf/0x2a0 [jbd]  <e09055b0> ext3_get_block+0x0/0x100 [ext3]

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c011ba7e> try_to_wake_up+0x6e/0x3d0  <c0190255> mpage_readpages+0x95/0x150

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <e09055b0> ext3_get_block+0x0/0x100 [ext3]  <e09046d0> ext3_readpages+0x0/0x20 [ext3]

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c0152cfd> __do_page_cache_readahead+0x17d/0x270  <e09055b0> ext3_get_block+0x0/0x100 [ext3]

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c014b8a0> file_read_actor+0x0/0xf0  <c014ebc5> filemap_nopage+0x2c5/0x3a0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c0158e62> __handle_mm_fault+0x132/0x900  <c02d8ffe> schedule+0x41e/0xcc0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c02dc30b> do_page_fault+0x3db/0x6f0  <c02dbf30> do_page_fault+0x0/0x6f0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c010420f> error_code+0x4f/0x60 

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000] Code: 90 8d 74 26 00 83 ec 08 89 74 24 04 89 c6 8d 40 10 89 1c 24 89 d3 e8 6a f3 18 00 8d 46 04 89 da e8 70 6a 09 00 85 c0 89 c1 74 0d <8b> 00 89 ca f6 c4 40 75 16 90 ff 42 04 90 ff 46 10 fb 8b 1c 24 

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000] EIP: [find_get_page+38/80] find_get_page+0x26/0x50 SS:ESP 0068:ce6c9ad0


```

With the new ubuntu out on Thursday - should I just leave this to correct itself then?

---

### Post by Kilz on 2007-10-16
> **auraithx said:**
> ```
sudo apt-get install audacity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Segmentation fault
glasgowm@glasgowm-desktop:~$ 
Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] Oops: 0000 [#19]

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] SMP 

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] CPU:    0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] EIP is at find_get_page+0x26/0x50

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] eax: 74756220   ebx: 000b6db2   ecx: 74756220   edx: 00000000

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] esi: c147c554   edi: 00000000   ebp: c147c440   esp: ce6c9ad0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] Process apt-get (pid: 24112, threadinfo=ce6c8000 task=c06c4030)

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] Stack: 00000000 000b6db2 c016c773 ef5cef5c 14e94300 003d77b4 ef5cef5c ce6c8000 

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]        c147c4ac c147c554 00568006 c147c554 00000000 00000008 c14063e0 c147c440 

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]        c016cb7f 000b6db2 00000000 00000000 00000000 ce6c8000 c147c4ac c147c554 

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000] Call Trace:

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c016c773> __find_get_block_slow+0x53/0x170  <c016cb7f> __find_get_block+0x9f/0x1a0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c016cca3> __getblk+0x23/0x2e0  <c016ccac> __getblk+0x2c/0x2e0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c016e950> __bread+0x10/0xa0  <e09045bc> ext3_get_branch+0x8c/0x100 [ext3]

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <e0904812> ext3_get_blocks_handle+0xa2/0xb20 [ext3]  <c0152c56> __do_page_cache_readahead+0xd6/0x270

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c014ba30> find_get_page+0x20/0x50  <c0182b58> __d_lookup+0x88/0x110

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c0182b58> __d_lookup+0x88/0x110  <c014ba30> find_get_page+0x20/0x50

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c016c7a9> __find_get_block_slow+0x89/0x170  <c014ba30> find_get_page+0x20/0x50

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c015390f> activate_page+0x8f/0xa0  <c0153a1d> mark_page_accessed+0x2d/0x40

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <e0905633> ext3_get_block+0x83/0x100 [ext3]  <c018f784> do_mpage_readpage+0x204/0x710

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <e08ef2df> __journal_file_buffer+0xbf/0x2a0 [jbd]  <e09055b0> ext3_get_block+0x0/0x100 [ext3]

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:12 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c011ba7e> try_to_wake_up+0x6e/0x3d0  <c0190255> mpage_readpages+0x95/0x150

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <e09055b0> ext3_get_block+0x0/0x100 [ext3]  <e09046d0> ext3_readpages+0x0/0x20 [ext3]

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c0152cfd> __do_page_cache_readahead+0x17d/0x270  <e09055b0> ext3_get_block+0x0/0x100 [ext3]

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c014b8a0> file_read_actor+0x0/0xf0  <c014ebc5> filemap_nopage+0x2c5/0x3a0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c0158e62> __handle_mm_fault+0x132/0x900  <c02d8ffe> schedule+0x41e/0xcc0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c02dc30b> do_page_fault+0x3db/0x6f0  <c02dbf30> do_page_fault+0x0/0x6f0

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000]  <c010420f> error_code+0x4f/0x60 

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000] Code: 90 8d 74 26 00 83 ec 08 89 74 24 04 89 c6 8d 40 10 89 1c 24 89 d3 e8 6a f3 18 00 8d 46 04 89 da e8 70 6a 09 00 85 c0 89 c1 74 0d <8b> 00 89 ca f6 c4 40 75 16 90 ff 42 04 90 ff 46 10 fb 8b 1c 24 

Message from syslogd@glasgowm-desktop at Tue Oct 16 15:07:13 2007 ...
glasgowm-desktop kernel: [17301594.836000] EIP: [find_get_page+38/80] find_get_page+0x26/0x50 SS:ESP 0068:ce6c9ad0


```

With the new ubuntu out on Thursday - should I just leave this to correct itself then?

Since you are running a test version , as a good community member [you should report all problems on launchpad]("https://bugs.launchpad.net/ubuntu") so they can be fixed. If you never tell the developers it may be a long time before it gets fixed.

---

### Post by auraithx on 2007-10-16
I'm not running a test version.

---

### Post by auraithx on 2007-10-17
fixed itself when I restarted.

---

