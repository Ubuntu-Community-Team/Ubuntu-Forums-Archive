---
title: "Solfege 3.0.2"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by mimsmall on 2007-03-03
Using Dapper 6.06. 
Installed Solfege 3.0.2 by synaptic. Opening Solfege gets this error message: The sound init failed: [Errno 2] No such file or directory: /dev/sequencer2.  You should cofigure sound from the 'Sound' page of the preferences window.

It is also possible that the OS sound setup is incorrect.

My music CDs and DVDs have no sound problems. 

I looked in /dev and no /sequencer directories.

I'm thinking that all required directories should be created during install.

Some one who has it working, please tell me how it went for you.

---

### Post by skinny honkie on 2007-03-19
Hi there - here's a fix for ya:

After installing solfege, install TiMidity as per the following guide:

[http://www.cs.cornell.edu/~djm/ubuntu/index_dapper.html#timidity](http://www.cs.cornell.edu/~djm/ubuntu/index_dapper.html#timidity)

Just do steps 1-5 unless you find step 6 absolutely necessary. Alternatively you could use the easyubuntu package to add midi support, then the guide above to add some extra patches.


Then go into Solfege, edit->preferences->sound setup, you should see under .midi file player a string like /usr/bin/timidity -idqq %s to verify that timidity is all set up ok.

Then, just select "use external midiplayer", then "apply changes and play test sound"

:-) Enjoy Solfege goodness

---

### Post by mimsmall on 2007-03-20
Thank you; Solfege now works, but :( clicking on Applications>Sound and Video>Timidity does not open Timidity. Which seems strange when Solfege works correctly.

---

