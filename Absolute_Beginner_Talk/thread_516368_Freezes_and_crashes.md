---
title: "Freezes and crashes"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by shockingelk on 2007-08-03
My hard drive on an Acer Aspire 5100 went kaput and I decided to try Linux on the new drive.

I installed from a Feisty Fawn DVD I'd burned. ForeFox worked fine, reuuning Evolution with an IMAP server caused the whole system to hang or crash.

So I made an install CD of Dapper Drake. Same thing - running Evolution caused hangs and cradhes. So I reinstalled, this time getting ThunderBird. Same problems.

Then I installed again, using ThunderBird in POP3. Same problems.

Each time, I'm letting the installer choose partitioni9ng, which it takes to use the whole (60 GB) disk.

Typically things start to go south starts with an error while saving "could not save file, check ymp directory. At other times, the toolbar chrome at top and bottom dissappearzs.

Sometimes it will display a command-line login after crashing.

What am I doing wrong?=Erilk

---

### Post by Jimmyfj on 2007-08-03
When you first installed Ubuntu did you then update the system with all updates available? This could be the first thing to try. If updating your system doesn't work please post the output error, this may help us to help you.

---

### Post by shockingelk on 2007-08-03
Yes, I did run the updates each time.

I'm not sure what you mean by the "output error". there are always 8-10 errors in the text part of startup, but I can't read them.

There's suspiucious lines in the kernal log:
Aug  3 00:14:11 erik-laptop kernel: [17179594.684000] hda_codec: invalid dep_range_val 0:7fff
Aug  3 00:14:11 erik-laptop last message repeated 92 times

and syslog:
Aug  3 02:55:54 erik-laptop kernel: [17181363.628000] hdb: status error: status=0x51 { DriveReady SeekComplete Error }
Aug  3 02:55:54 erik-laptop kernel: [17181363.628000] hdb: status error: error=0x20 { LastFailedSense=0x02 }
Aug  3 02:55:54 erik-laptop kernel: [17181363.628000] ide: failed opcode was: unknown

lots of these in evms engine
Aug 03 02:26:34 erik-laptop _3_ Engine: engine_open_object: Open of /dev/evms/.nodes/ram5 failed with error code 22: Invalid argument

Thanks ...

---

### Post by shockingelk on 2007-08-03
What log files would be useful to see?

---

