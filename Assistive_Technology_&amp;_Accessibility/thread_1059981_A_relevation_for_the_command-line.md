---
title: "A relevation for the command-line?"
date: 2009-02-04
forum: Assistive Technology &amp; Accessibility
---

### Post by AICollector on 2009-02-04
I've been thinking about this a lot, and am so sure it's such a good idea I've posted it to the GNOME forum and GNOME 3 scratchpad; here's my idea;

There is a gulf between the command line and the graphical user interface. The first is effective and fast, but requires the user understands the computers terms.

The second is much more friendly, but is limited in what it can do and how it can do it.

So, I propose we use a natural language interface for part of the system.
I could ask my computer to do something (for example; formatting the external HD) simply by typing "Please format my external hard-drive"

I feel this is a better and more natural (read: close to Ubuntu's philosophy) way then having to learn to move about a GUI (and of course having the knowledge to understand what the GUI's menu options mean) and of having to get to grips with the command-line.

In short: a natural language system would give the user the best of both worlds, effectiveness and a natural method of using the machine.

---

### Post by sisco311 on 2009-02-04
Something like [gnome-do]("http://do.davebsd.com/")?

---

### Post by AICollector on 2009-02-04
No, not at all; GNOME-DO, whilst a very good app, can't understand natural language, not in the way I'm suggesting.

Alternate commands (moving away from sysadmin tasks) could be:

"Tell David I can't come to the party tonight" (mailto: David. Message: I can't come to the party tonight)

"What are apples?" (connect to Wikipedia/START)

"Do I have any appointments today?" (intergrate with Evolution or another time-manager)

"Read this out to me" (uses Festivel to read the active window)


Going back to sysadmin tasks, wouldnt a Conversational Interface be better then a command-line interface?

---

### Post by sonicb00m on 2009-02-04
The reason natural language will never work is because it's ambiguous in so many cases. Configuration files are not ambiguous.

What might have context to you has no context to a computer. It will have to be programmed to make assumptions and assumptions will naturally end in error and frustration for the user.

H "Please format my external hard-drive"
C "er which one?"
H "Er... the blue one"
C "Which one is that then?"
H "The one sitting on the left side to me"
C "No idea what you mean"
H "Install camera driver"
C "Installed, jeez what ugly an *********** you are"

---

### Post by sirjoebob on 2009-02-04
While not a bad idea in theory (and a very cool, Star Trek way to interact with a computer). There is to much decision-making left up to the computer. Lets looks at your examples:

> "Tell David I can't come to the party tonight" (mailto: David. Message: I can't come to the party tonight)
If I have a "David" in my Pidgin, Skype, and email contacts, how does it decide? Computers aren't made to parse language, just do commands. 

> "What are apples?" (connect to Wikipedia/START)
How would it know to check wikipedia instead of Google search? 

Take a look at Ubiquity from Mozilla labs. It does some of what you are talking about. It is kind of like Gnome-do for web things like Google Maps, etc. good idea, but hard to put into practice.

---

### Post by donkyhotay on 2009-02-04
What you're describing is borderline artificial intelligence, not a new idea but (so far) a complete pipe dream. While yes if ever done it would be great but I don't think the complexities of natural language is something that can be coded. Look at your own examples:

"Tell David I can't come to the party tonight" (mailto: David. Message: I can't come to the party tonight)

compared with:

"Ask david what time the party is" (mailto: David. Message: When is the party?)

So two completely different keywords (tell/ask) need to be coded for what is essentially (as far as the computer is concerned) the exact same task, sending an Email. This will lead to an extremely bloated program if you imagine all the other ways people could (will) ask their computer to send an Email to someone, and thats just one task. A program like this you also can't just think 'oh, they'll learn the specific key commands and only use those'. The whole point of people using this type of system is so they *don't* have to learn anything new. Then you also have to have the computer determine what the user meant when a command is vague (at least by computer standards). Just think of someone asking

who is david?

The computer is then left with trying to figure out what the user meant. Does the user want to search wikipedia for 'david'? Does the user want to run the whois command for the user david? Also in some cases it would be harder. Sure it's easy to think you can just tell your computer 

Backup data to server

and expect it to do so however the computer will need to know what data to back up, what server to back it up to, and how you want it backed up. Admittedly you could configure all that beforehand so it will happen whenever you say it but if you are going to go through all the effort of setting it up that way you might as well set up a cron job too so you don't even have to say it. As I said before, it would be great if computers understood language the way we do but they currently can't. Artificial intelligence of the type you're looking for is something that I believe can't be coded but will probably have to actually be taught (just like with kids) to machines *much* more complex then we currently have available to us. Like say, about the complexity of an actual human brain.

---

### Post by sonicb00m on 2009-02-04
> **donkyhotay said:**
> Artificial intelligence of the type you're looking for is something that I believe can't be coded but will probably have to actually be taught (just like with kids) to machines *much* more complex then we currently have available to us. Like say, about the complexity of an actual human brain.

This is right. That's what neural networks aim to do where the computer learns the correct answer. However, these are still very simple in terms of what the human brain does.

---

### Post by AICollector on 2009-02-04
I dont just collect AI, I build them. I know it's limitations, and I know that to do this, a program need only look out for keywords, I don't need HAL 9000.


@sirjoebob: I had in mind an email setup for that, mainly because I think it'd be quite odd for a system to be designed that may or may not deleiver a message (as is the case over some IM networks)


@donky: I've helped build such an AI, it's not impossible, but the hardware requirments are. :P
(look up: Jeeney AI, fantastic bot, currently turning Wikipedia into an ontology)

the 'david' example I thought would be rather simple, if there is more then one David, it asks me which one I mean.

I will admit the Wikipedia idea is troublesome, but possible. I would suggest this system be integrated into the deskbar.

backup data to server is a bit vauge, which is why I think the system would be mostly one way, it could still ask; "What server?" and have a sort of 'built-on-the-spot' wizard for that.

Come on, people, a modern computer can run about 2000 indepedant ALICE bots, (this laptop, for instance, is able to run 1707) and for some odd reason, your telling me thats impossible?

---

### Post by sirjoebob on 2009-02-04
Have you looked at Ubiquity yet? It uses closer-to-spoken-word commands like "email this to mom" to send an email with the selected text to gmail user contact named "mom."

If you are convinced that this can be done. then do it. I am not discouraging, just doubtful that we have the potential right now to make this anything other than a secondary list of commands the end-user must learn. Great idea though.

---

### Post by AICollector on 2009-02-04
I will look into it. I just don't see what would be so 'bloated' about a system that listens for keywords (minus, of course, the list of other words for the same thing, not really bloat)

Any further refinement of this idea?

---

### Post by sirjoebob on 2009-02-04
> **AICollector said:**
> I will look into it. I just don't see what would be so 'bloated' about a system that listens for keywords (minus, of course, the list of other words for the same thing, not really bloat)

Any further refinement of this idea?

My suggestion would be to look at how ubiquity works. It allows custom commands that are easily configured. I would stick with single syntax for commands. ie one spoken-word command per action just to keep things simple. Look to existing projects that mimic this functionality and I would love to hear if you do anything with this. My email and twitter account are listed in my signature and I would be very interested in hearing if you do anything with this.

---

### Post by Dies on 2009-02-04
This would be pretty cool...

But really, I'd settle for a decent video editing program and a decent DVD maker ( even though DVD is almost dead now ) that just work...

Yeah, I don't see that happening either... at least not anytime soon.

:p

---

### Post by donkyhotay on 2009-02-04
> **AICollector said:**
> Come on, people, a modern computer can run about 2000 indepedant ALICE bots, (this laptop, for instance, is able to run 1707) and for some odd reason, your telling me thats impossible?

Not impossible, just impractical. I'm not saying don't do it, even if it doesn't work right the way you describe you may develop something useful. Even if you don't you would have learned quite a bit about developing language recognition software. Also, you may surprise us (and the world) by actually developing a natural language recognition system which would be awesome, especially if it was open source! (c:

---

### Post by xqtr on 2009-03-09
I accidentally read this post and i understand how difficult is the command line for new linux users, especially for the ex-windows users.

Because i had/have ;) the same problem, i recently build an application for the terminal/console that will narrow the gap between the command line and the GUI.

It is actually a text mode application that uses a menu driven system to execute simple linux commands. Most of the commands that are built in, are used for solving linux problems (mounting drive, internet connection etc.). There are also some guides/tutorials that explain how the user complete some tasks. Take a look at: [http://sourceforge.net/projects/concom/](http://sourceforge.net/projects/concom/)

I know that is not what you are looking for, but it may help ;)

---

### Post by lukjad on 2009-03-09
I'm not a fan of thinking computers. I saw too many of them on Star Trek go crazy and start taking over. Also, does please need to be added? Also, what about slag? How does one update it? What if it changes with time? Also, language changes quickly in some place, but not in others. Some places will have one type of slang, another won't. Also, if you make the parameters too "loos" to understand what you mean, this will cause inaccuracies.

---

