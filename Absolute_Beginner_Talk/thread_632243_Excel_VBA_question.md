---
title: "Excel VBA question"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Lazlo2 on 2007-12-05
:confused:
Hi all,
I am losing interest in computing, I cannot get my projects to run the way they ought to. 
I am talking about my spreadhseets and Excel VBA macro that runs a process that works just fine for me, when it works under the current OS
 ( XP )


Question is,
Can I run Excel VBA macro, in particular a piece of code that is a Dynamic Web Query in real time under a Ubuntu OS ?

My understanding of computer program jargon is litraly Zilch above VBA.
But from what I have read here so far, look interesting.


Thanks.

---

### Post by rickycodie on 2007-12-05
you could probably do it with virtualbox or vmware. 

[http://virtualbox.org](http://virtualbox.org)

the other is in the repo's

---

### Post by OffAxis on 2007-12-05
how complicated is your dynamic web query?
(select the .iqy file, right click and 'Edit in Notepad')
you may be able to perform a similar function in openoffice or koffice.

---

### Post by dwanders on 2007-12-05
VBA wont run under Linux. You could possibly get into running MS Office in Wine or Crossover Office but that sounds like much more than you are wanting to get into. 

If you truly want to try out Linux / Ubuntu - you should consider replacing your Office suite completely and learn how to do your Spread sheet in the completely Free Open Office. And I think Open Office uses its own macro language. 

Sorry but that is the cold hard truth. IMHO - Office and Visual Basic (for applications & the development suit) are the main reasons that people are afraid to move to a better OS like Linux. And it is a shame. Open Office is a very viable alternative to MS Office and it is also a shame more people do not use it.   

my 2 cents, take it or leave it.

---

### Post by Lazlo2 on 2007-12-05
Thanks for the replies and I'll try to answer them, or ask a bit more.

rickycodie.
(Excuse the waffle, just trying to convey a picture of things)

Not sure I understand the concept of virtualization. I could always try as there are at least 4 computers laying dormant due to constant upgrades over the years.
.....................,
 Most of my programs are a series of calculators,in a complex real-time, fast with deadlines, no room for error,typos or emotional decision environment..,
doing the same basic calculation, but as we know, MS keeps changing things, and what once worked well in DOS for example may not be adaptable today as far as software is concerned.
My calculations however MUST have a live source data-feed. The early DOS versions of my calculators, the numbers and reference details were typed in. 
The same process was later fully automated and was then built using a Firebird Server, database and script editor when XP first arrived.
My original request at the time was to have it developed in Linux, because of all the drama prior to XP at the time. I had enough of MS, but was convinced XP will work, and it did, for that single purpose.

The key was in the scripting and is all the user needed to learn to do,
provided there were some tutorial, and there was none on that specific project.
That fell to due to it being private development project and the result of that  project is now in a coma due to BSoD and the developer has "gone away".
Therefore, no server to re-install and simply run my scripts !

When I had nothing to work with and bored as hell, I re-created the entire process, JUST to get the live data feeds off the net and to do the same dam calculation using Excel VBA, but was shown the web query part on
how to achieve this. Sanity was then re-stored cos I spat the dummy when I found out I could not re-install the server on the new HD.

Once I got the live data back in at my disposal, the rest just fell in place.

Now I find Excel will jam up, it IS documented that this bug DOES happen
and the "MS Gurus" make me sound as if I am crazy for wanting to "fix" the problem in a unorthodox manner. 
That is, will someone write me a BAT file to just shutdown Excel and re-open the same file and resume the macro when it does a On Error.
Instead of Cntl/Alt/Delte to close Excel ???

Remember, the concept of things is to eliminate repetitious manual tasks.
If anyone wants the page where this glitch is explained, let me know and I'll post the MS "support" web page. It has something to do with explorer temp file being filled up after too many web queries.
Well, why not just simply empty the temp file ? duh !
No, it has to freeze excel and can only shut down Excel.Exe via task manager, then re-open the workbook and re-start the macro manually.
It really kills the buz of watching my process and number crunching work, then when it suits it can send the calculated data back out to the net, via E-mail when testing, but ultimately a specific 3rd party Application is the real destination the calculated data needs to go to.
It really sux, when "progress" has actually slowed me down.

I don't see why all this high tech stuff is required except in my case and a few others that I know simply require the computer to do all the repetitious number crunching in real time, 10 hours minimum per day on
over apporximately 160-200 events currently happening  out in the real world.

The numbers being crunched is not the science, it's getting it done in such a way to be able to sit back and watch the graph.
----------------------,
OffAxis
I am not sure if I can guage the complexity of the query itself.
It's once the numbers and data are in calculation process, then it gets complex, but I have that sorted and the logic is in place. I do not need to re-create anything or look for something new as in what to do with a number cruncher. 
.....................,

dwanders
You hit the nail, I have tried Open Office and it would be my option, but at the time, a few months ago the web query seemed to be lacking when I tried.
Once Open Office  web query can do  be what Excel is , then I can discard my OS's and move onto Linux. I can't wait for this to happen and I guess I may have some testing logistics to run repetitious web queries.
But yeah, that is the way to go if I know Open Office will do continued web query non stop.
--------------,

Ultimately, the Server idea that will run the script would  be the way to go, as I already have the scripts, or the "logic" to do the math, run 3rd paty Applications AND "talk" to Excel or Open Office for finer detailed caclculations.

It just seems to go around in circles.

Thanks.

---

