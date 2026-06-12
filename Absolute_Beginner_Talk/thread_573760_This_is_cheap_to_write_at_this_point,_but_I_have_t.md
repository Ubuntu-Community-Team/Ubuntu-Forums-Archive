---
title: "This is cheap to write at this point, but I have to post it"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by mister_lister on 2007-10-11
I know this forum is dedicated to technical resolutions, but I want to make a political\financial commitment.

First of all, thanks to all of you, I am fully off the microsoft tit. I have a fully functional "windows\gui" operating system. The only thing I can not do is get streaming windows media,such as radio station broadcasts (I am a die hard leo laport listener on KFI 640 am). I'm sure one of you will clue me in on how to get those streams.

Anyway that is trivia I can always turn on the radio!. What I want to say in this post is that I am making a commitment. IF I win the California Lottery and it is in the millions, I will commit to supporting GNOME, UBUNTU, and KUBUNTU for many years. If it is enough, I will give a million dollars a year to each of those projects. 

I play the lottery religiously, eventually I will win something. Already I have made purchases through the store front at ubuntu. I really believe in this project and want it to grow. I encourage you to do the same. Even free has a price.

I kid you not, I can do everything with my linux os, that I could with M$ crap - and more. Not only that I don't have to worry about VIRUSES, WORMS, SPYWARE, and other nasty crap I have a whole OS to explore and discover, I feel like a kid in candy store. I feel guilty, got so much for so little. All it cost me was a download and some time confering with you and configuring. 

So the commitment stands. I will advocate for linux. I will buy things. I will continue to donate time, money and energy to this and other projects until something comes to fruition and we see the monopoly end that m$ has currently.

An OS is supposed to be free and Painless, let's make it happen.

---

### Post by tgalati4 on 2007-10-11
>sudo apt-get install streamtuner

>sudo apt-get install winninglotteryticket

---

### Post by mister_lister on 2007-10-12
I'll try the "sudo apt-get install streamtuner" bit, but the lottery ticket fetcher seems a bit far fetched....(I'll probably try it too just for sh*ts and giggles)

---

### Post by mister_lister on 2007-10-12
The streaming tuner was installed but the "winning lottery ticket " didn't work... Go figure... oh well back to the old math work.

---

### Post by Shazaam on 2007-10-12
Along the same vein..
```
apt-get moo
```

---

### Post by tgalati4 on 2007-10-12
Winning lottery ticket numbers are public records.  Some smart folks have written analysis programs to examine a particular state's lottery for less-random patterns.  Play those numbers and you can increase your chances.

And no, there is no package called winninglotteryticket, unless you write it yourself.

Of course in Linux, you can write your own ticket.

---

### Post by Jorge on 2007-10-12
Maybe with:

```
sudo apt-get install IShouldWinTheLotteryBecauseIHaveAGreatPlanForExpendingThatBunchOfMoney --InAnUnbeatableMoralWay 
```
If it works, let us know, :)

---

### Post by Old *ix Geek on 2007-10-12
> **tgalati4 said:**
> Some smart folks have written analysis programs to examine a particular state's lottery for less-random patterns.  Play those numbers and you can increase your chances..Those things can't work. What it always boils down to is that ANY ball has as much chance of being picked as any OTHER one.  (A good analogy is flipping a coin--even if 'heads' comes up a thousand times in a row, 'tails' STILL has an equal chance of coming up the next time.)  So it doesn't matter how many times a number has (or hasn't) come up before; there's simply no correlation between that and what will happen in the future.  It's a nice thought, though...and I wrote a program like that about 15 years ago, just for fun, knowing full well it COULDN'T help. :wink:

---

### Post by anewguy on 2007-10-12
I remember back in about 1982 or 1983 while working as a systems programmer/sysadmin in a very large shipyard in San Pedro, CA having to write a "wheeling" program for a group of lottery players at work (my boss actually told me to do this).  They had good documentation and everything for how the wheeling should work, and had a guy doing it manually.  They decided they needed help when the guy goes and gives the same set of numbers 7 times for 1 run of the lottery!:)

So, if you can't download a package :)  just be sure not to duplicate the entire set of numbers for the same day lottery!:)

---

### Post by mister_lister on 2007-10-12
streamtuner didn't work, firefox is wanting a plugin, but cannot find a suitable plugin for windows media player. That is the "format\plug in" this radio station uses, windows bloody media player.When will the monopoly end. Anyways, I will fool around and find an alternative way of getting that stream. Any help will be appreciated.

---

### Post by Steveway on 2007-10-12
You need to install the mplayer-plugin for firefox.
You can find it in the repos.

---

### Post by mister_lister on 2007-10-12
OK, that sounds logical. What I tried already was launching streamtuner and digging into the website to find the actaual url of the player. I added it to streamtuner and it still didn't work.
It gave me an error that it couldn't find the xmms directory. exact error message is "Failed to execute child process "xmms" (no such file or directory)."


What is the method for finding the "mplayer-plugin" for firefox, do I use "apt-get install", "synaptic" or some other method, remeber I am a baby, newbie, linux retard, windows tit leach at this point so I need things spelled out for my inept little mindless gui brain. I can do command line if it is spelled out, so all I have to do is type in the terminal.

Thanks in advanced.

---

### Post by mister_lister on 2007-10-12
I did a search on synaptic for "mplayer plugin", it came up with a file and a bunch of dependencies. I installed all of it and then opened firefox and went to the web site radio station that had the live feed. It loaded the commercials fine but the content did not come through. So, I went to another radio station and went to the live broadcast and everything worked perfectly, I am c urrently listening to a preacher whine about god, but the fact is that mplayer works for some live windows media player feeds but "KFI AM 640" doesn't work properly. I don't know how to get this live feed other than switching on the old radio. Any thoughts would be appreciated.

---

### Post by Steveway on 2007-10-12
Can you provide us a link?
So we can test it ourselves.

---

### Post by kostkon on 2007-10-12
> **mister_lister said:**
> OK, that sounds logical. What I tried already was launching streamtuner and digging into the website to find the actaual url of the player. I added it to streamtuner and it still didn't work.
It gave me an error that it couldn't find the xmms directory. exact error message is "Failed to execute child process "xmms" (no such file or directory)."


What is the method for finding the "mplayer-plugin" for firefox, do I use "apt-get install", "synaptic" or some other method, remeber I am a baby, newbie, linux retard, windows tit leach at this point so I need things spelled out for my inept little mindless gui brain. I can do command line if it is spelled out, so all I have to do is type in the terminal.

Thanks in advanced.

As taken from [RestrictedFormats - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RestrictedFormats"):

> Ubuntu 7.04
[LIST]
[*]Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.
[*]To play most DVDs you'll need the libdvdcss2 package. This package is available using [Medibuntu]("https://medibuntu.org/"). This is a third party package, and not supported by Canonical.

Note: If DVD playback fails, and you've never played any DVD before on your system, you may need the regionset package to initially set the drive's region.

[*] Some external codecs may be needed in order to play certain proprietary formats such as Apple Quicktime or RealVideo. These external codecs are available in the third-party repository of [Medibuntu]("https://medibuntu.org/").
[/LIST]


To add the *medibuntu* repository to your software sources list, as taken from [Medibuntu - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Medibuntu"):

> 
Ubuntu 7.04 "Feisty Fawn":

```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```


Then go to *Synaptic*, find the package named *w32codecs* and install it.

If you do the above, you will be able to playback most of the video and audio formats (including *Windows Media*).

I saw from your posts that you wanted to listen from web radios that broadcast in *Windows media*, and you said you wanted a plugin for *Firefox*.

If you use *Totem*, in order to  install the plugin for *Firefox*, just go to *Synaptic* and search for *totem-mozilla*.Then select it and install it. Do similarly, if you use *Mplayer* or *VLC*, by installing the *mozilla-mplayer* and* mozilla-plugin-vlc* packages respectively.

Note that if you use *VLC*, you don't need to install any of the codecs above, because *VLC* has its own. Although, I don't know if it has a good support for *Windows Media*.

Also note that if you use *Totem* and you don't have good success of listening to some web radios that you find on webpages, where the *Firefox Totem plugin* is being used, try to install *Totem-Xine*; maybe you will have better results. Thus, go to *Synaptic* and search for the *totem-xine* package and install it. Your version of *Totem*, which uses the *Gstreamer* framework, will be replaced with a different version that uses the *Xine* framework.

---

### Post by motoperpetuo on 2007-10-12
Lottery=A tax for people who are bad at math.

---

### Post by cheetaux on 2007-10-12
> **tgalati4 said:**
> Winning lottery ticket numbers are public records.  Some smart folks have written analysis programs to examine a particular state's lottery for less-random patterns.  Play those numbers and you can increase your chances.

Actually this is a common fallacy.  The outcome of any random event is totally independent of the previous results.   Just because a set of lotter numbers have already have already won does not reduce the chances of those numbers winning again.

---

### Post by mister_lister on 2007-10-12
By the way, I am using 6.06 (dapper drake fully updated) so the posts about fiesty fawn (etc) do not apply (I won't upgrade my hardware cries).

The lottery is not a tax for people bad with math, I PROTEST, it is a tax for people who are specifically inept at statistics (or who just want to gamble and perhaps win something eventually (which I remind you is a statistical probability if not a possibility)). 

I'm good at algebra and some calculas. Never took statistics.

ANY WAY.... back to the last post I made... Some windows media live radio players work on my linux install NOW and others don't, is this the fault of the website or mplayer for not having codecs or something? Do I need something else? I guess this is really a conversation I should have with the webmaster at KFI, figure out what versions he is posting and what I need.

Here is the web site I am trying to listen to live broadcasts from:

[http://www.kfi640.com/main.html](http://www.kfi640.com/main.html)

click on the "listen live" link and see what you get. Report results and what you think I should do.

---

### Post by AMDBuntu on 2007-10-13
If you win please

sudo apt-get paypal me thanks!

:popcorn:

---

### Post by tgalati4 on 2007-10-13
You can edit streamtuner's preferences to use any media player for each type of stream.  There must be a dozen different protocols of streams.  Xmms is a simple music player that can handle a lot of different formats (assuming you have gstreamer good, bad and ugly codecs installed).

>sudo apt-get install xmms

Pick the streams that you really want to listen to and then figure out the best player to use to listen to them.

For help on a particular stream type, do a forum search and you will find lots of suggestions on how to decode a particular stream.

---

### Post by ryanVickers on 2007-10-13
> **tgalati4 said:**
> >sudo apt-get install winninglotteryticket
hey, it didn't work! :(

---

### Post by ryanVickers on 2007-10-13
> **Jorge said:**
> Maybe with:

```
sudo apt-get install IShouldWinTheLotteryBecauseIHaveAGreatPlanForExpendingThatBunchOfMoney --InAnUnbeatableMoralWay 
```If it works, let us know, :)

nope
> 
E: Command line option --InAnUnbeatableMoralWay is not understood

;)

---

### Post by Soarer on 2007-10-13
> **mister_lister said:**
> 

Here is the web site I am trying to listen to live broadcasts from:

[http://www.kfi640.com/main.html](http://www.kfi640.com/main.html)

click on the "listen live" link and see what you get. Report results and what you think I should do.

No good for me. It doesn't like the fact that I am not in the USA :)

Sorry - can't help.

---

### Post by Steveway on 2007-10-13
> **Soarer said:**
> No good for me. It doesn't like the fact that I am not in the USA :)

Sorry - can't help.

Same here.

---

### Post by n3tfury on 2007-10-13
listening to some guy named george right now.  firefox under gutsy gibbon beta.  i had to install a plugin.  several to choose from, but chose the vlc multimedia plugin because me loves vlc.  also, i used the user agent switcher add on for firefox which fools sites into thinking you're using IE.  by the way it took a good 30 seconds for that stream to start for me.

*edit* it works in default Firefox without agent switching.  lol, these peeps are talking about aliens and checking for burn marks on her shed or something from a spaceship landing.  too whacko for me.  enjoy your station.

---

