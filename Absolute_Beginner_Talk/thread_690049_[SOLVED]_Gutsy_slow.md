---
title: "[SOLVED] Gutsy slow?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-02-07
I don't where else to post this, and wanted to see if others have noticed similar.

I did a fresh install of Gutsy right after it was released and ran it for a couple of months.  Everything seemed considerably slower than in Feisty.  No matter what I did videos were choppy, voip was choppy, etc..  I finally just went back to a fresh install of Feisty.  These apparent speed issues have disapeared since reverting back to Feisty.  Now, I run an old slow machine - a PIII-500 with 512mb of memory - perhaps Gutsy is meant for more modern robust hardware?

Any feedback would be appreciated!

Dave  :)

---

### Post by talsemgeest on 2008-02-07
It could be some issues with compiz fusion.

Go System>Preferences>Appearance>Visual Effects and select "None"

Hope this helps :)

---

### Post by gtdaqua on 2008-02-07
u installed gutsy on P-III with 512MB RAM? It shouldnt be suddenly slower. How much swap have you configured? type "free" to know your swap size and its utilization. post the output. it shoud be like this:

```

user@gutys71:~$ free
                       total       used       free     shared    buffers     cached
Mem:        904720     890864      13856          0      82408     468852
-/+ buffers/cache:     339604     565116
Swap:      2819368          0    2819368

user@gutys71:~$


```

---

### Post by gtdaqua on 2008-02-07
> **anewguy said:**
> I don't where else to post this, and wanted to see if others have noticed similar.

I did a fresh install of Gutsy right after it was released and ran it for a couple of months.  Everything seemed considerably slower than in Feisty.  No matter what I did videos were choppy, voip was choppy, etc..  I finally just went back to a fresh install of Feisty.  These apparent speed issues have disapeared since reverting back to Feisty.  Now, I run an old slow machine - a PIII-500 with 512mb of memory - perhaps Gutsy is meant for more modern robust hardware?

Any feedback would be appreciated!

Dave  :)

just noticed that you have over 650 beans with "Skinny Soy Caramel Ubuntu" and asking such a question??? wats wrong?

---

### Post by anewguy on 2008-02-07
> **gtdaqua said:**
> just noticed that you have over 650 beans with "Skinny Soy Caramel Ubuntu" and asking such a question??? wats wrong?

Hey - I can answer some of the simpler questions, which I have done, and I can sure ask them!:)

---

### Post by Blutack on 2008-02-07
Tracker & deskbar are probably the main culprits.
First thing to get disabled on a fresh gutsy install for me.

---

### Post by cybertron3000 on 2008-02-07
Regular Ubuntu is by far the most lightning quick OS I've used.  I wasted money on upping my RAM to 750MB, when Ubuntu uses only 143MB of it!  I could have had the same lightning response by leaving it at 256MB.

---

### Post by cybertron3000 on 2008-02-07
When I mentioned "regular" Ubuntu, I mean the Gutsy Gibbon version.

---

### Post by anewguy on 2008-02-07
I appreciate the feedback!   Since I am running Feisty now it is a little difficult ( :) ) to get the information again.  Judging from everyone's responses, I would suspect I must have hosed something up (like THAT'S a first !! :) ).

Thanks for the feedback - I'll probably try Gutsy again soon, maybe on a spare drive so I don't kill my Feisty yet!  :)

---

### Post by cybertron3000 on 2008-02-07
It's nice to be of some help - I'm only about a month into this whole Ubuntu thing, starting with Gutsy.  Can't believe how quick and tunable it is compared to the Windows XP I ditched.  Hope you keep the faith.

---

