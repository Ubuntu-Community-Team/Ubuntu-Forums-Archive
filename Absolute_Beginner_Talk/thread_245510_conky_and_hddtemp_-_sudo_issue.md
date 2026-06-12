---
title: "conky and hddtemp - sudo issue"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by neocookie on 2006-08-27
As part of some updates to my system, I'm configuring conky to show what I think is useful to me. Being that I run dapper on my laptop I'd like to check the temperature of my system while its running.

I've installed conky, and have it configured with the usual stuff. I've also installed hddtemp, and running "sudo hddtemp -q /dev/hda" will show me the current temp.

However, I need conky to have access to this program. I could use "${execi 10  hddtemp -q /dev/hda}" to pull the temperature in, but unfortunately sudo is required to run the program.

I've tried running hddtemp as a daemon, but it doesn't produce the same (correct) output as on the command line.

Any suggestions as to how I can get this working?

Thanks.

---

