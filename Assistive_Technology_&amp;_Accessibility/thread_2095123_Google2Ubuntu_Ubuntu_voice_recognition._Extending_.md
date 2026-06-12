---
title: "Google2Ubuntu: Ubuntu voice recognition. Extending voice macros/scripts to use Google"
date: 2012-12-15
forum: Assistive Technology &amp; Accessibility
---

### Post by bboyjkang on 2012-12-15
Google2Ubuntu - Google voice recognition on Ubuntu – Extending VoiceCode, Vocola, Unimacro, Dragonfly et al. (voice program extensions/macros/scripting) to use Google voice recognition  
 

 **Introduction**

 **Hi**

 Hi! I want to spark a discussion about whether Google voice recognition could be a third major alternative in voice recognition along with Dragon NaturallySpeaking and Windows Speech Recognition, and whether the current third-party extensions for Microsoft and Nuance's products can also be made to support Google.  
 

 **VoiceCode**

 1 of those add-ons is VoiceCode, which “is an Open Source initiative started by the National Research Council of Canada, to develop a programming by voice toolbox. The aim of the project is to make programming through voice input as easy and productive as with mouse and keyboard.” ([http://sourceforge.net/projects/voicecode/](http://sourceforge.net/projects/voicecode/)). I originally decided to post this write-up in the VoiceCode forums ([http://tech.groups.yahoo.com/group/VoiceCoder/](http://tech.groups.yahoo.com/group/VoiceCoder/)), as a lot of discussion seems to be happening there.  
 

 **A proposal for everyone**

 The post first started as an appeal to VoiceCode users to consider new development options. A project that caught my eye whilst searching for voice recognition alternatives was a program called Google2Ubuntu. Therefore, I thought that this post also belonged in the Ubuntu forums (Assistive Technology & Accessibility: [http://ubuntuforums.org/forumdisplay.php?f=145](http://ubuntuforums.org/forumdisplay.php?f=145)). The write-up then ballooned to a solicitation of Ubuntu users and the general public to sample voice recognition,   came out as a conversation with Google, and became a rant in certain places. Those are the reasons for the length (I don't know how to create a working table of contents, or convert and transfer rich text formatting from LibreOffice yet; sorry, but you'll need to Ctrl+F to jump).
 

 **Long post**

 Warning: this post is very lengthy, long-winded, overblown, and not organized well. (average time to read according to Wolfram Alpha: 32 minutes). Disclaimer: I am biased toward Google. I hope it will still be worth your time reading.  
 
```

               **Table         of Contents**
     
     Introduction    
     Hi    
     VoiceCode    
     A proposal for     everyone    
     Long post    
     Reddit, and James     McClain's script    
     My first reddit     comment:    
     My second reddit     comment, in response to a question about what Ubuntu offers Google:    
     James McClain:    
     Google2ubuntu    
     “Google2Ubuntu     is a free tool (GPLv3) to use the Google voice recognition on     Ubuntu.”    
     project-google2ubuntu    
     sourceforge    
     [FONT=Tahoma]&#65279;Benoit     Frappa/benoit franquet/benoitfra1's YouTube page     
     Google2Ubuntu     post on the French Ubuntu discussion board/forum:     
     Google2Ubuntu     post in the English Ubuntu discussion board/forum:    
     Other projects     that are using Google voice recognition    
     Speech2Text    
     Google Voice API    
     Fun with Google     Speech Recognition Service    
     Incentives for     Google supporting/allowing Google2ubuntu    
     Google and Ubuntu     are allies    
     Goobuntu    
     Android's new     ally against the iPhone: Ubuntu    
     Google and     Microsoft    
     Google vs. Apple     + Nuance    
     “Why Apple     Could and Should Buy Nuance”    
     Nuance is less     cooperative    
     Responses from     the VoiceCode forum:    
     “Vlingo     Announces Victory in Patent Trial with Nuance Communications -     Jurors Found No Evidence of Infringement”    
     Nuance Plays     Hardball in Voice Recognition    
     The Patent, Used     as a Sword    
     Google vs.     Nuance    
     A Nuanced Case     Against Nuance    
     Current usage of     voice recognition    
     Programmers and     voice recognition    
     Comparing the     extensions    
     Code vs.     dictation    
     General     population and voice recognition    
     Neural networks    
     Touch screens    
     Low-cost eye     tracking    
     Gaze Group     open-source eye tracker     
     Gaze Group Gaze     Tracker 2.0 Demo/Screencast     
     High-cost eye     tracking    
     Gaze Group forums         
     Pareto principle    
     Acknowledging     command-and-control, instead of just dictation    
     Infrequent     commands    
     More common     commands    
     Very common     command: PgDn    
     Setting up for     PageDown and text-editing     
     Common commands     and text-editing by voice    
     Access/mnemonic/accelerator/underlined     keys    
     Coding by voice    
     Counter-arguments    
     Command-and-control     vs. dictation    
     Casual vs.     Pareto    
     User comfort    
     A look to     Microsoft    
     Microsoft is a     proponent of accessibility     
     Current state of     Microsoft accuracy    
     Vocola 3 to     Vocola 2    
     Price and demand    
     Lobbying Ubuntu     users    
     Nuance and     Linux/Ubuntu    
     Trends in desktop     speech technologies    
     Microsoft trends    
     Nuance trends (in     attitude and support)    
     Google trends    
     Android adoption         
     Google and     improvements in voice recognition    
     To Google, voice     recognition is part of its broader ecosystem    
     Nuance vs.     open-source    
     Google and     open-source    
     Google culture    
     Nuance and     accessibility    
     Google and     accessibility    
     Google and     Python    
     Dragonfly: speech     recognition framework     
     Google I/O 2011:     Python@Google    
     Cost    
     Developer     relations with Nuance    
     Pessimism     
     Cooperation and     open-source are aggressive     
     Exponential     technologies, and the advancement of society    
     Uncertainty and     vulnerability of projects    
     Plant the seeds    
     Positive feedback     loop    
     Collaborate    
 
 

 **Reddit, and James McClain's script**

 I first discovered a YouTube video, and submitted it to Reddit: Voice Recognition on Ubuntu with Google's servers without Chrome – [1:04] [http://www.reddit.com/r/Ubuntu/comments/13wnv8/voice_recognition_on_ubuntu_with_googles_servers/](http://www.reddit.com/r/Ubuntu/comments/13wnv8/voice_recognition_on_ubuntu_with_googles_servers/)
 

 **My first reddit comment:**

 For anyone interested, here is some more information from the author's Google plus page:  
 

 Google+ post for a previous video, which is his first Ubuntu voice recognition video:  
 

 [https://plus.google.com/u/0/109027253925936825710/posts/SCvAjdtz2Wy](https://plus.google.com/u/0/109027253925936825710/posts/SCvAjdtz2Wy)
 

 [http://www.youtube.com/watch?v=uM2Yb-PwP6o](http://www.youtube.com/watch?v=uM2Yb-PwP6o)  
 

 >+David Landry Yes, keep me informed if you do anything cool with it though.
 >[http://pastebin.com/r1rzzL9H](http://pastebin.com/r1rzzL9H)&#65279;  
 >
 >I probably wouldn't work on this alone since I would not be able to make a front-end (not one that looks any good). So I would probably wait until some people who know how to do that start working on it, and then join in.  
 >
 >I agree about the voice recognition tool, it would help a lot if ubuntu had one.
 >
 >There are some made already([http://julius.sourceforge.jp/en_index.php/](http://julius.sourceforge.jp/en_index.php/)), but none of them compare to google's accuracy, and this should easily work everywhere, all that needs to be built is an action dictionary. &#65279;  
 

 Google+ post for the second video, and the target of the reddit submission:
 [https://plus.google.com/u/0/109027253925936825710/posts/Tc21k66vVmQ](https://plus.google.com/u/0/109027253925936825710/posts/Tc21k66vVmQ)
 

 >+Srinivas Gowda I explained my tricks if you expand the post. I can make a video to go into more depth. Basically, it uses a chromium window as a frontend, and then a python script to recognize the actual actions. I used the chromium window because it already does all the voice and microphone stuff for me.  
 >
 >However, Ideally I want to make this without needing that. So I either need to learn how to interact with the audio server on linux. Or find a programmer who does that can help make the frontend.
 

 Georgi KaravasilevAug 5, 2012
 +2
 Well, I am a designer, so if you need design help for the front-end I can conjure up something pretty ^^ :)
 &#65279;
 **My second reddit comment, in response to a question about what Ubuntu offers Google:**

 [–]AllRadioisDead
 Then maybe it's time for Canonical to make a deal with Google.
 [–]Illivah
 by offering what exactly?
 

 [–]bboyjkang
 Dragon NaturallySpeaking and Windows Speech Recognition both ask you if they can collect your corrections to improve future recognition. I'm sure Google could use more data.
 

 **Google’s Data Advantage Over Apple’s Siri**
 

 >"When Eric Schmidt was still chief executive of Google, I asked him what the company owned that would make it particularly hard for any emerging search contender to wipe Google out. Spell check, he said. Google had observed the spelling mistakes and corrections typed into billions of queries, and had a vast understanding of what people really meant when they typed like thsi.".
 >
 >"While the Jelly Bean version of Voice Search is new, Google’s linguists have five years of data on billions of pronunciations. A year ago, just for the English language, Google had a database of 230 billion word strings, and had worked on 23 other languages, based largely on 411 and related voice-based search products, including an earlier version of Voice Search. It’s another spell check.".
 [http://bits.blogs.nytimes.com/2012/07/19/googles-data-advantage-over-apples-siri/](http://bits.blogs.nytimes.com/2012/07/19/googles-data-advantage-over-apples-siri/)
 

 **Help improve transcription quality**
 

 >"The messages you donate may be listened to, manually transcribed by us and/or used to gauge transcription improvements over time, but they will never be made public or used for any other purpose than improving the transcription quality. And if you're feeling generous, you can go back to old messages you previously rated and donate those, too! Thanks in advance for your help.".
 [http://googlevoiceblog.blogspot.ca/2009/12/help-improve-transcription-quality.html](http://googlevoiceblog.blogspot.ca/2009/12/help-improve-transcription-quality.html)
 

 **Voxforge**  
 

 By the way, Voxforge ([http://www.voxforge.org/](http://www.voxforge.org/)) is a project that is  
 >"set up to collect transcribed speech for use with Free and Open Source Speech Recognition Engines (on Linux, Windows and Mac). We will make available all submitted audio files under the GPL license, and then 'compile' them into acoustic models for use with Open Source speech recognition engines such as CMU Sphinx, ISIP, Julius and HTK (note: HTK has distribution restrictions).".
 

 I'm partially disabled, and I need voice scripting (Vocola) to operate the computer. My migration to Ubuntu would be impeded without adequate speech recognition. If it's possible to integrate, Google's speech recognition could remove an advantage that Windows has, and conceivably bridge the gap until an open source speech recognition engine becomes sufficient.  
 

 Don't dismiss speech recognition just yet; forget dictation; use your voice for the commands! Vocola has similar, easy-to-use syntax like Autohokey and IronAHK.
 

 **James McClain:**

 “One problem? Well, I tried to learn how to record audio myself, but I quickly found out that the libraries for interacting with the microphone were more complicated then I expected. So I built a small chromium window and connected it to a mini python server to work as a native desktop assistant.

But James, you said you can do this all **without** google chrome!

You can, I promise, I just need some help with someone who knows how to do this:

1. Get sound from the microphone.
2. Automatically stop when a person has stopped talking.
3. Clean up the sound as much as possible and..
4. Put it into the Speex codec.
Finally it will be sent to google's servers and from there everything is pretty easy. ”.
 

 “+Sidarth Dasari Well, my main problem is, I need some way to get sound from the users microphone, C, C++ or python would be best. I've tried to learn it myself but had some trouble, so if anyone can find a way to do this and is willing to show me the code, I can start making a real voice control thing for ubuntu and put it in the software center for everyone.

This is what I need:
1. Record audio from the user.
2. Stop recording when the user stops talking.

That's all, if anyone reading this can make a program that does this, we can make something pretty cool.”.
 

 **Google2ubuntu**

 On the second video on Google plus , a benoit franquet commented on James McClain's post:
 benoit franquet Sep 30, 2012
 +3
 I have sent you a message on youtube in order to present google2ubuntu. I hope you receive it.
 

 Searching up on Google2Ubuntu, I found the following information from various websites (the sites are French, but if you have Chrome, it does automatic translation):
 

 **“Google2Ubuntu is a free tool (GPLv3) to use the Google voice recognition on Ubuntu.”**

 [http://doc.ubuntu-fr.org/google2ubuntu](http://doc.ubuntu-fr.org/google2ubuntu)
 [http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fgoogle2ubuntu&act=url](http://translate.google.com/translate?sl=auto&tl=en&js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fgoogle2ubuntu&act=url)
 

 **project-google2ubuntu**

 [http://code.google.com/p/project-google2ubuntu/](http://code.google.com/p/project-google2ubuntu/)
 

 **sourceforge**

 “This utility allows you to control Ubuntu through voice recognition google. The GUI is an indicator compound and the remainder is administered by glade2script”.
 [https://sourceforge.net/projects/google2ubuntu/](https://sourceforge.net/projects/google2ubuntu/)
 

 **[FONT=Tahoma]&#65279;Benoit Frappa/benoit franquet/benoitfra1's YouTube page  **

 Demonstration videos: [http://www.youtube.com/user/benoitfra1/videos?sort=p&flow=grid&view=0](http://www.youtube.com/user/benoitfra1/videos?sort=p&flow=grid&view=0)
 

 Translated video description:
 “This shell script allows you to use voice recognition that Google offers on Ubuntu. You can easily add custom commands. Looking for more information GoogleUbuntu. The latest version is now 3.1. I modified the function for sending mails using thunderbird now. You can now change the wallpaper, do some research on youtube, wikipedia, you can also display the TV program of the evening.novelty Other management orange bouquet of channels that can be easily run, saying any sentence containing the name of the channel. Eg, I want to see France 2, France 2 You want to look I added support for all weather cities. graphical interface has been redone entirely with glade2script for ease of use. ideas if you related add functions to pass on the ubuntu forum fra playlist video was created to show news and a thread on the forum is open ubuntu at this address: [http://forum.ubuntu-fr.org/viewtopic.php?](http://forum.ubuntu-fr.org/viewtopic.php?) id = 804211 & p = 16The Deb is available here: [http://dl.dropbox.com/u/25779406/google2ubuntu_3.1_all.deb](http://dl.dropbox.com/u/25779406/google2ubuntu_3.1_all.deb)”.
 

 **Google2Ubuntu post on the French Ubuntu discussion board/forum:  **

 Welcome > Forum > "Tips and useful scripts" > [Script] google voice recognition. [http://forum.ubuntu-fr.org/viewtopic.php?id=804211](http://forum.ubuntu-fr.org/viewtopic.php?id=804211). (I believe that most of the discussion takes place here; the thread has 18 pages).
 

 **Google2Ubuntu post in the English Ubuntu discussion board/forum:**

 Benoit Frappa/benoit franquet/benoitfra1 also posted the project in the English Ubuntu discussion board/forum: Ubuntu Forums > The Ubuntu Forum Community > Ubuntu Specialised Discussions > Assistive Technology & Accessibility > Speech recognition script with Google.  
 “and a deb file here
Lien de téléchargement de google2ubuntu
 

But I don't want people to use this version; I just want to give an idea in order to make somebody of you able to convert this french deb files in an english ready deb ”.  
 [http://ubuntuforums.org/showthread.php?t=2048466](http://ubuntuforums.org/showthread.php?t=2048466)
 

 **Other projects that are using Google voice recognition**

 **Speech2Text**

 “Using the power of ffmpeg/flac/Google and ruby here is a simple interface to play with to convert speech to text.
 Using a new undocumented speech API from Google with the help of this article: mikepultz.com/2011/03/accessing-google-speech-api-chrome-11
 We’re able to provide a very simple API in Ruby to decode simple audio to text.”.
 [https://github.com/taf2/speech2text#readme](https://github.com/taf2/speech2text#readme)
 

 **Google Voice API**

 “For using the Google Voice API and the script you need to have the following package installed on your freerunner:  
 SoX [http://sox.sourceforge.net]("http://sox.sourceforge.net/") for converting WAV into FLAC files  
 WGET [http://www.gnu.org/s/wget/](http://www.gnu.org/s/wget/) for submitting the FLAC file to the Google Voice API  
 SED [http://sed.sourceforge.net/](http://sed.sourceforge.net/) for extracting the recognized text in the returned string of the Google Voice API  
 Install the packages from the repositories of the freerunner Distributions.”.
 [http://wiki.openmoko.org/wiki/Google_Voice_Recognition](http://wiki.openmoko.org/wiki/Google_Voice_Recognition)
 

 **Fun with Google Speech Recognition Service**

 “In this article, I write some tips to use Google speech recognition API in Windows application with direct recording voice from audio input devices.”.
 [http://www.codeproject.com/Articles/338010/Fun-with-Google-Speech-Recognition-service](http://www.codeproject.com/Articles/338010/Fun-with-Google-Speech-Recognition-service)
 

 I don't know how James McClain's project is related to benoit franquet's project, if both are related to the 3 project links I posted it above (the Ruby one, OpenMoko, and Google in Windows), or if they overlap. I shouldn't be wildly spamming links without at least understanding a bit them, but I'm just seeing if anything helps.
 

 **Incentives for Google supporting/allowing Google2ubuntu**

 I barely comprehended anything that was being discussed in the VoiceCode thread, “Proposed changes to VoiceCode, so far...” ([http://tech.groups.yahoo.com/group/VoiceCoder/message/6675](http://tech.groups.yahoo.com/group/VoiceCoder/message/6675)), and I don't know what's feasible, but I want to comment on Google voice recognition, quoting some of what I read:
 

 As mentioned in the link that I posted above, Google could always use more data to increase accuracy. More third-party tools available can entice people to try using voice recognition, thus sending more data to Google. It's not just private voice data. More public, online text = more opportunities to improve language translation services, and learn the context of language. There's also a reduction in effort required by individuals to correct errors.
 

 **Google and Ubuntu are allies**

 Google2ubuntu makes Ubuntu better. Ubuntu competes with Microsoft, and Google competes with Microsoft, so a better Ubuntu helps Google.
 

 **Goobuntu**

 Chris DiBona, the program manager for open-source software at Google, said “I think Ubuntu has captured people’s imaginations around the Linux desktop,” and “If there is a hope for the Linux desktop, it would be them”.
 

 Also, “close to half of Google’s 20,000 employees use a slightly modified version of Ubuntu, playfully called Goobuntu.”.
 [http://www.nytimes.com/2009/01/11/business/11ubuntu.html?pagewanted=all](http://www.nytimes.com/2009/01/11/business/11ubuntu.html?pagewanted=all)
 

 **Android's new ally against the iPhone: Ubuntu**

 “That's why when Canonical announced and demonstrated Ubuntu for Android at Mobile World Congress in February, it generated a lot of interest across the mobile industry. Users liked the idea of a more full-featured desktop than Motorola's Webtop. Android phone makers liked the idea of using the software to build high-powered multi-purpose devices and make more money off smartphones accessories like desktop docks. And, wireless carriers loved the idea of powerful smartphones running desktop-level applications that will demand more data than ever.”.
 

 “When Ubuntu is loaded on an Android phone, the two platforms share the same Linux kernel, so it's not like running two operating systems. The two pieces act like complementary partners. The Android phone functions normally when used as a smartphone or when making calls, but when it docks then the Ubuntu desktop pops up and acts like a standard computer. You can open a desktop Web browser, but you can also install and run standard Ubuntu desktop software for photo editing, word processing, etc.”.
 [http://news.cnet.com/8301-1035_3-57424335-94/androids-new-ally-against-the-]("http://news.cnet.com/8301-1035_3-57424335-94/androids-new-ally-against-the-iphone-ubuntu/")[iphone-ubuntu/]("http://news.cnet.com/8301-1035_3-57424335-94/androids-new-ally-against-the-iphone-ubuntu/")
 

 **Google and Microsoft**

 “I switched back [to Dragon] because Microsoft appears to have abandoned desktop speech recognition, and WSR was never quite as good as Dragon”. “The main drawbacks of WSR for me are recognizing background noises as little words”. (I can verify this. Too often, an exhale of breath outputs the word, “And”).
 

 If Ubuntu has better voice recognition, Microsoft might feel the pressure to improve their own desktop, television, and mobile recognition.
 

 If, in addition to Ubuntu, a desktop Google voice recognition is on Windows, Google still gets the data, and general goodwill of users.
 

 **Google vs. Apple + Nuance**

 Apple's Siri uses Nuance's technology: [http://techcrunch.com/2011/10/05/apple-siri-nuance/](http://techcrunch.com/2011/10/05/apple-siri-nuance/)
 

 **“Why Apple Could and Should Buy Nuance”**

 “Apple can use Nuance to give it a technology edge well into the future. Apple now holds a slight lead with its Nuance-powered, Siri voice-based interface for the iPhone 4S. Yet, Samsung is catching up and making inroads with its own voice-controlled Galaxy phones, also with help from Nuance.
 

 Samsung is already threatening to overtake Apple's lead in the global smartphone market later this year, as consumers snatch up Samsung models with their relatively larger screens. Apple cannot afford to let Samsung also beat it in voice technology.
 

 Buying Nuance would nip that threat, helping Apple keep the best voice-recognition technology for its own hardware going forward – a competitive edge it can also leverage versus Google”.
 [http://www.benzinga.com/trading-ideas/long-ideas/12/08/2793236/why-apple-could-and-should-buy-nuance](http://www.benzinga.com/trading-ideas/long-ideas/12/08/2793236/why-apple-could-and-should-buy-nuance)
 

 “[Nuance] hates that we're using [Natlink] because it competes with their "Pro" product, which is one of the reasons they now say you're not supposed to use it unless you have a pro license”. If these wrappers/extensions (Dragonfly et al. etc.) can flourish under Google, they will continue to improve unabated. Since your projects somewhat compete with Nuance (by providing free substitutes for their $500 Dragon NaturallySpeaking professional version), this helps Google because you're indirectly competing with Apple, which is a rival of Google.  
 

 **Nuance is less cooperative**

 **Responses from the VoiceCode forum:**

 “Nuance has at best a policy of benign neglect when it comes to the NatLink APIs”.  “Nuance slowly changes their code base and tramples NatLink APIs”. “I don't see this slow degradation process stopping or reversing”. “Nuances inability or unwillingness to fix long-standing bugs that seriously hurt developers (natural text, grammar parser, etc.)”. “The dependency of VoiceCode on Natlink is something that always vaguely worried me, in a "what if" kind of way. But this fear is becoming a bit more concrete every year.”. “We are at significant risk from the abuse from Nuance”.
 

 **“Vlingo Announces Victory in Patent Trial with Nuance Communications - Jurors Found No Evidence of Infringement”**

 “Specifically, Nuance alleged that two Vlingo commercial systems infringed the '295 patent: the Vlingo/IBM system and the Vlingo/AT&T Watson system. Vlingo uses speech recognition systems developed by IBM and AT&T to build its products. The jury found neither system infringed. Ironically, the IBM speech recognition system used in the Vlingo solution was acquired by Nuance in 2009, and Vlingo is a customer of Nuance's for the IBM engine. So, in alleging the Vlingo/IBM system infringed, Nuance was claiming a customer of its own technology infringed its patents – even though this use was consistent with the terms of the license.”.
 

 “"The ruling by the jury is further vindication that Nuance cannot compete in the market, said Dave Grannan, president & CEO, Vlingo. "We are happy to report that with this latest ruling, Nuance's record remains perfect in patent infringement trials, they haven't won any.".
 

 "It's distasteful that Nuance engages in this abuse of the legal system because it clogs our courts and stifles innovation," said Mike Phillips, CTO, Vlingo.  "We hope this ruling demonstrates to the market and our customers that Vlingo won't be bullied by these tactics and will continue to deliver on innovation.".
 

 “In an absurd allegation, Nuance also asserted that several experiments Vlingo and AT&T conducted in conjunction with AT&T's Watson Speech Engine infringed the '295 patent. These joint experiments were for research purposes only, and never resulted in a commercial product. The jury also ruled that these experiments did not infringe the '295 patent.”.
 

 "It's a real measure of the desperation of Nuance," said Grannan. "This is clearly an aggressive step by Nuance to attempt to attack AT&T's technology through Vlingo and demonstrates Nuance will go to the ridiculous extreme in its patent troll behavior to try to stifle innovation in our industry.".
 

 "It's a new level of absurdity," said Mike Phillips, Co-founder and Chief Technology Officer, Vlingo. "Nuance actually used an academic research paper from Interspeech 2011, a well known research conference, to accuse Vlingo of running infringing experiments. I have been attending these conferences for decades and have never seen anything this ridiculous.".
 [http://www.prnewswire.com/news-releases/vlingo-announces-victory-in-patent-trial-with-nuance-communications-127381353.html](http://www.prnewswire.com/news-releases/vlingo-announces-victory-in-patent-trial-with-nuance-communications-127381353.html)
 

 **Nuance Plays Hardball in Voice Recognition**

 “Ricci's critics say he's lawsuit happy and uses strong-arm tactics to weaken innovative rivals so he can buy them on the cheap or put them out of business. Over the past decade, Nuance, based in Burlington, Mass., has sued eight companies over alleged patent infringements. It hasn't won any judgments and lost one. On at least four occasions, it purchased smaller companies it had sued. "Competing with Nuance is like having a venereal disease that's in remission," says Dave Grannan, CEO of Vlingo, a speech-recognition startup that's involved in five Ricci-related lawsuits. (Nuance has four suits against Vlingo; Vlingo has one against Nuance.) "We crush them whenever we go head-to-head with them. But just when you're thinking life is great—boom, there's a sore on your lip."”.
 [http://www.businessweek.com/magazine/content/11_22/b4230037736600.htm](http://www.businessweek.com/magazine/content/11_22/b4230037736600.htm)
 

 **The Patent, Used as a Sword**

 ““We had spent $3 million to win one patent trial, and had five more to go,” said a former Vlingo executive who spoke on condition of anonymity because he had signed confidentiality agreements. “We had the better product, but it didn’t matter, because this system is so completely broken.””.
 

 “Large companies with battalions of lawyers can file thousands of pre-emptive patent applications in emerging industries. Start-ups, lacking similar resources, will find themselves easy prey once their products show promise.”.
 

 “Start-ups are where progress occurs,” he said in an interview. “If you spend all your time in court, you can’t create much technology.””.
 [http://www.nytimes.com/2012/10/08/technology/patent-wars-among-tech-giants-can-stifle-competition.html?pagewanted=all](http://www.nytimes.com/2012/10/08/technology/patent-wars-among-tech-giants-can-stifle-competition.html?pagewanted=all)
 

 **Google vs. Nuance**

 **A Nuanced Case Against Nuance**

 “Nuance (NUAN) is not a patent troll. It is a patent dragon, having sued and bought out most of its competitors in voice recognition.”.
 

 “Like patent trolls, Nuance would be hurt by stricter interpretation of software patents. Patents are coming under increasing scrutiny. Many economists are saying they should disappear altogether. The legal monopoly Nuance has built up through years of lawsuits and acquisitions could fade.”.
 

 “Google already participates in cloud computing, voice recognition and translation, so Google already competes with Nuance in theory. But practically speaking, Google is just beginning to polish its product in this area. We're talking about the company that makes Priuses drive themselves, well enough to be allowed on public roads.”.
 [http://seekingalpha.com/article/927661-a-nuanced-case-against-nuance](http://seekingalpha.com/article/927661-a-nuanced-case-against-nuance)
 

 **Current usage of voice recognition**

 “first, I would like to ask the following question: 'What is it that's preventing people from adopting VoiceCode?' This is a question that has been puzzling me for many years, and I don't have a definitive answer.”.
 

 I'm an absolute beginner when it comes to programming and voice recognition, and I have no credentials, but I'll take a guess as to what can cause lower rates of usage, and what might help.
 

 **Programmers and voice recognition**

 **Comparing the extensions**

 If you're talking about why programmers that use voice recognition for coding don't choose VoiceCode, I'm not qualified to answer, but there was some reasoning already in the thread on how Vocola might be less complex and powerful, but more user friendly (making assumptions based on miniscule knowledge of Vocola and no knowledge of VoiceCode).
 

 **Code vs. dictation**

 If you're talking about why programmers that use voice recognition in general don't use it for coding, I'm guessing that computer code isn't an output that is produced as often. When you compare the occurrence of code to dictation and commands, the appearance of code is probably a really small fraction.
 

 My favorite and most used AutoHotkey script that I've used for many years consists of 3000 characters and 500 words, and I tinker with it maybe once in several months. This post that I'm making right now is approaching 2000 words, and an online post like this happens more often than once in several months.
 

 It could be because a lot of the vocabulary of natural language is established. I read that things in code can be hard to pronounce e.g. “C++ ... practitioners seem to have never heard of vowels”. User-created things have to be constantly defined in voice dictation shortcuts? (by the way, there's a Autohotkey script to immediately make a Hotstring out of a selection. Is this needed or done in voice scripting?).
 

 **General population and voice recognition**

 If you're asking about why people don't use voice recognition, I read that some people don't want to use voice recognition because it's not accurate enough (it would become more accurate if more people used it), but it's getting better all the time:
 

 **Neural networks**

 "Leading breakthroughs in speech recognition software at Microsoft, Google, IBM"
 

 “The idea that they had was to use a technology in a way patterned after the way the human brain works – it’s called deep neural networks.”.
 [http://www.news.utoronto.ca/leading-breakthroughs-speech-recognition-software-microsoft-google-ibm](http://www.news.utoronto.ca/leading-breakthroughs-speech-recognition-software-microsoft-google-ibm)
 

 **Touch screens**

 Nowadays, since much more people are using voice recognition on devices that use touch screens, so in addition to using voice commands to correct, they can select text by touch, which may be quicker than the mouse in certain instances. This can help make people stick with voice recognition.
 

 **Low-cost eye tracking**

 “In Eye Control, A Promise To Let Your Tablet Go Hands-Free”
 

 “Just over a year ago, Johansen and his colleagues spun off into The Eye Tribe, a company with the goal of making it possible for all people to control mobile devices with their eyes.”.
 

 “The Eye Tribe software is unique, because it relies only on standard low-cost components that are easily integrated into next generation smartphones and tablets.”.
 

 “The company plans to release the technology at no cost to other software developers early next year, Alstrup Johansen said. "We are releasing software developing kits to developers so they can actually start developing applications. We intend to give it away, it won't cost anything," he said.”.
 [http://www.youtube.com/watch?v=ef0qLb8-4k8](http://www.youtube.com/watch?v=ef0qLb8-4k8)
 [http://www.france24.com/en/20121024-danes-develop-eye-control-software-phones-tablets](http://www.france24.com/en/20121024-danes-develop-eye-control-software-phones-tablets)
 

 ** Gaze Group open-source eye tracker  **

 “The ITU Gaze Tracker is an open-source eye tracker that aims to provide a low-cost alternative to commercial gaze tracking systems and to make this technology more accessible. It is developed by the Gaze Group at the [IT University of Copenhagen]("http://www.itu.dk/") and other contributors from the community, with the support of the [Communication by Gaze Interaction Association]("http://www.cogain.org/") (COGAIN).”.
 [http://www.gazegroup.org/downloads/23-gazetracker](http://www.gazegroup.org/downloads/23-gazetracker)
 

 ** Gaze Group Gaze Tracker 2.0 Demo/Screencast  **

 “A short demo of the upcoming ITU Gaze Tracker 2.0, a full feature open source eye tracker. The video shows the configuration and setup of the software. ”.
 [http://www.youtube.com/watch?v=75KRipM2W5c](http://www.youtube.com/watch?v=75KRipM2W5c)
 

 **High-cost eye tracking**

 Compare that to an eye tracking product that I saw a year back:
 EyeTech TM4 USB Eye Tracking Hand-Free Mouse
 Price: $7,480.00  
 

 **Gaze Group forums  **

  On the Gaze Group forums, people, using the open-source software + a cheap webcam, are posting their eye tracking setups that go as low as $40.
   [http://www.gazegroup.org/forum](http://www.gazegroup.org/forum)
 

 Eye tracking would definitely complement voice recognition, as mouse commands can be one of the slowest commands to execute (“Mouse Grid” causes me to break out in hives). It could probably be faster than Select-and-Say in some cases (assuming that you can activate a control or text by mouse-over).
 

 **Pareto principle**

 As noted, the average person is not producing as much dictation output (and people really aren't producing as much code). I may submit an online comment once every few weeks, and only tinker with a script and macro once every couple months.  
 

 In addition to the frequency of an individual's output, there is the distribution of output that comes from the general population, which is based on a pareto principle/distribution.
 

 “The most active 2% of Wikipedia users made 73.4% of edits in 2006 (including maintenance and administrative edits”.  
 

 “As usability godfather Jakob Nielsen broke it down in 2006: “In most online communities, 90% of users are lurkers who never contribute, 9% of users contribute a little, and 1% of users account for almost all the action.””
 [http://thewayoftheweb.net/tag/pareto-principle/](http://thewayoftheweb.net/tag/pareto-principle/)
 

 If every single person on the planet just produced 1 word, that would create 6,973,738,433 words ([https://www.google.com/publicdata/explore?ds=d5bncppjof8f9_&met_y=sp_pop_totl&tdim=true&dl=en&hl=en&q=world%20population](https://www.google.com/publicdata/explore?ds=d5bncppjof8f9_&met_y=sp_pop_totl&tdim=true&dl=en&hl=en&q=world%20population)). It would take 17601 days/48.22 years for any given person to read all those words ([http://www.wolframalpha.com/input/?]("http://www.wolframalpha.com/input/?i=how+long+Read+6%2C970%2C000%2C000+words")[i=how+long+Read+6%2C970%2C000%2C000+words]("http://www.wolframalpha.com/input/?i=how+long+Read+6%2C970%2C000%2C000+words")).  
 

 Basically, people spend more time consuming information than producing information, and a majority of the population produces only a small amount of information.
 

 **Acknowledging command-and-control, instead of just dictation**

 **Infrequent commands**

 I think a possible solution to get more people to use voice recognition is to encourage voice commands. While a person may not create dictation or code on a daily basis, computer commands are often used everyday. However, it's not just any kind of voice command that is of consequence. If you look at a lot of videos that demonstrate voice commands, such as the Ubuntu video above, they usually involve opening a program, going to a file directory, a finding a website. I can only speak to my own personal activity, but the problem is that I open a program less than 10 times a day, and go to a favorite website or folder less than 20 times a day.  
 **More common commands**

 A few of the Vocola commands that are of further interest, as they may appear more often, are:
 

  [COLOR=#000000][COLOR=#355e00]Use[/COLOR]   [COLOR=#000080]<n>[/COLOR]     = TaskBar.SwitchToButtonNumber([COLOR=#000080]$1[/COLOR]) pointerHere();[/COLOR]
  [COLOR=#000000]e.g. say “[COLOR=#355e00]Use[/COLOR] [COLOR=#000080]3[/COLOR]”.[/COLOR]
  [COLOR=#000000]Activate the 3rd application in the taskbar.[/COLOR]
 

  [COLOR=#000000]Show Desktop = {Win+d};[/COLOR]
 

 [COLOR=#355e00]Window[/COLOR] ([COLOR=#000080]Maximize=x | Minimize=n | Restore=r[/COLOR]) = SendSystemKeys({Alt+Space}) [COLOR=#000080]$1[/COLOR];
 e.g. say “[COLOR=#355e00]Window[/COLOR] [COLOR=#000080]Maximize[/COLOR]”.
 [COLOR=#355e00]Window[/COLOR] ([COLOR=#000080]Maximize=x[/COLOR]) =  
 SendSystemKeys({Alt+Space})  # windows menu
 [COLOR=#000080]x[/COLOR];                # access key for maximize
 

 Switch Window = SendSystemKeys([COLOR=#b80047]{Alt+Tab}[/COLOR])[COLOR=#008080]pointerHere()[/COLOR];
 Switch Window =  
 SendSystemKeys([COLOR=#b80047]{Alt+Tab}[/COLOR]) # switch window
 [COLOR=#008080]pointerHere()[/COLOR];            #  click to give it focus
 

 **Very common command: PgDn**

 I use WhatPulse ([https://whatpulse.org//](https://whatpulse.org//)), which is a free program that counts the amount of keys, mouseclicks, and the distance that your mouse moves (I have repetitive strain injuries/RSI/tendinosis, and I use the program to limit myself.). In a typical day, and excluding mouse clicks, it will display that the number of keys pressed are around 2000. If the other commands amount to only a couple 100 touches, what makes up all the rest of it? It's page down! (PageDown or PgDn). Unless you're using the scroll wheel, it should be by far the most used action. Since people are usually consuming information rather than producing information, it would make sense to promote “reading” or “consumption”commands. E.g.
 [COLOR=#004a4a]agoras[/COLOR]|[COLOR=#800000]balisaur[/COLOR]|[COLOR=#6b0094]capuchin[/COLOR]|[COLOR=#ff420e]diluvia[/COLOR] ... = [COLOR=#23ff23]{PageDown}[/COLOR];
 [COLOR=#004a4a](term | optionalWords)[/COLOR]|[COLOR=#800000](term | optionalWords)[/COLOR]|[COLOR=#6b0094](term | optionalWords)[/COLOR]|([COLOR=#ff420e]term | optionalWords[/COLOR][COLOR=#ff420e])[/COLOR] ... = [COLOR=#23ff23]action[/COLOR]
 (below the command is the Backus Normal Form/grammar for context)
 Any one of the alternative wordson the left can be usedto execute “Page Down”.
 

 [COLOR=#0066cc]agoras[/COLOR]|[COLOR=#83caff]balisaur[/COLOR]|[COLOR=#808019]capuchin[/COLOR]|[COLOR=#666666]diluvia[/COLOR] ... = [COLOR=#579d1c]{PageDown}[/COLOR];
 [COLOR=#0066cc](words | variable | range | menu)[/COLOR]|[COLOR=#83caff](words | variable | range | menu)[/COLOR]|[COLOR=#808019](words | variable | range | menu)[/COLOR]|[COLOR=#666666](words | variable | [/COLOR][COLOR=#666666]range | menu)[/COLOR] … = [COLOR=#579d1c]words | reference | call[/COLOR]
 

 [COLOR=#0066cc]agoras[/COLOR]|[COLOR=#83caff]balisaur[/COLOR]|[COLOR=#808019]capuchin[/COLOR]|[COLOR=#666666]diluvia[/COLOR] ... = [COLOR=#579d1c]{PageDown}[/COLOR];
 [COLOR=#0066cc](words)[/COLOR][COLOR=#579d1c]|[/COLOR][COLOR=#83caff](words)[/COLOR][COLOR=#579d1c]|[/COLOR][COLOR=#808019](words)[/COLOR][COLOR=#579d1c]|[/COLOR][COLOR=#666666](words[/COLOR][COLOR=#666666])[/COLOR][COLOR=#579d1c] … = words[/COLOR]
 

 [http://vocola.net/v3/FormalGrammar.asp](http://vocola.net/v3/FormalGrammar.asp)
 

 (Also, in addition to being monotonous, I think that constantly saying the same spoken term, such as “Page Down”, makes one more prone to voice strain).
 

 (For generating ideas for terms, an online tool to find words that start with a letter: [http://www.scrabblefinder.com/starts-with/](http://www.scrabblefinder.com/starts-with/)).  
 

 **[FONT=Calibri, sans-serif]Setting up for PageDown and [FONT=Calibri, sans-serif]text-editing **

 I use AutoHotkey (for Linux, use Autokey or IronAHK) to quickly select text:  
 *Left::Send {LButton 2}    ; Left arrow key to double-click to select a word.
                 ; Asterisks means it can be used while modifiers are held down.
 

 *Up::                ; Up arrow key to shift-click to extend the selection contiguously.
 Send {Shift down}
 sleep 200
 Send {Lbutton}        
 sleep 200
 Send {Shift up}
 return
 

 Down::^c            ;  Down arrow key to copy
 (I can also make use of the “Copy = {Ctrl+c}” voice command)
 

 Ditto (open source clipboard manager. [http://ditto-cp.sourceforge.net/](http://ditto-cp.sourceforge.net/)) can be used to gather multiple clipboard copies. After pasting all the text collected in Dittoto Libreoffice, the text has a consistent size and font, and centered the way that I like. The text is in 1 document, so “PageDown” is primarily the command that is necessary to maneuver through the document. As soon as people are satisfied with voice recognition substituting for such common actions, it will open the door to exploring other commands that are less common.
 

 **Common commands and text-editing by voice**

 More importantly, the text is edible, and I can do things such as putting each sentence on a new line if I want. (This can be done with a regular expression: s/\. /.\n/g).
 s/    # substitution
 (    
 \. /    # end of sentence is “period” “space”.
 .\n/    # replace with “period” “manual line break”
 )    
 /g    # global substitution
 /x    # free-spacing mode to ignore whitespace between regex tokens

This could help you read better, and is similar to how people use things like the pprint Python module to help read longer, nested data structures, or the jsonpickle Python library for serialization and deserialization of complex Python objects to and from JSON.

e.g. of pprint
>>> stuff = ['spam', 'eggs', 'lumberjack', 'knights', 'ni']

>>> pp.pprint(stuff)
 [   ['spam', 'eggs', 'lumberjack', 'knights', 'ni'],
     'spam',
     'eggs',
     'lumberjack',
     'knights',
     'ni']

   

You can now utilize voice commands that can set you up for text-editing such as:
 

 (including variable definitions for context)
 [COLOR=#355e00]<n> := 0..100[/COLOR];
 [COLOR=#000080]<direction>  := Left | Right | Up | Down[/COLOR];
 [COLOR=#355e00]<n>[/COLOR] [COLOR=#000080]<direction>[/COLOR]       = {[COLOR=#000080]$2[/COLOR]_[COLOR=#355e00]$1}[/COLOR];
 e.g. say “[COLOR=#355e00]4[/COLOR] [COLOR=#000080]Down[/COLOR]”.
 Output: {[COLOR=#000080]Down[/COLOR]_[COLOR=#355e00]4[/COLOR]}
 “Down arrow” key 4 times.
 

 [COLOR=#800000]<modifierKey> := Shift | Control=Ctrl | Alt | Alternate=Alt | Win | Windows=Win[/COLOR];
 [COLOR=#008000]<k> := <actionKeyNotArrow> | <characterKeyNotLetter>[/COLOR];
 [COLOR=#800000]<modifierKey>[/COLOR] [COLOR=#008000]<k>[/COLOR] [COLOR=#ff0000]Times[/COLOR] [COLOR=#5e11a6]<2to99>[/COLOR] = {[COLOR=#800000]$1[/COLOR]+[COLOR=#008000]$2[/COLOR]_[COLOR=#5e11a6]$3[/COLOR]};
 e.g. say “[COLOR=#800000]Shift[/COLOR] [COLOR=#008000]Up[/COLOR] [COLOR=#ff0000]Times[/COLOR] [COLOR=#5e11a6]8[/COLOR]”.
 Output: {[COLOR=#800000]Shift[/COLOR]+[COLOR=#008000]Up[/COLOR]_[COLOR=#5e11a6]8[/COLOR]}
 Select 8 contiguous lines up.
 

 I now have an additional and possibly easier way to navigate and select text, and I can do some things more efficiently, such as folding/hiding/deleting material that I already understand, or tagging/bookmarking information that I don't understand (or deleting sections that are irrelevant, such as a lot of what's in my post, as I tend to go off on a tangent).
 

 **Access/mnemonic/accelerator/underlined keys**

 Commands that activate accelerator keys can substitute for the commands with semantic names.  
 

 To input a “select all” command in LibreOffice:
 Select All = {Ctrl+a}a
 or
 Select All = {Alt+e}a
 Select All = ({Alt+e}    # Edit menu
         a    # access key for Select All
        &nbsp;);
 e.g. say “Select All” (Ideally, you want to say the semantic command, “Select All”, and not something like “Control a”).
 

 To input a “select all” command without saying “select all”:
 [COLOR=#ff0000]<modifierKey> := Shift | Control=Ctrl | Alt | Alternate=Alt | Win | Windows=Win[/COLOR];
 [COLOR=#9966cc]<key> := <actionKey> | <characterKey>[/COLOR];
 [COLOR=#000080]Press[/COLOR] [COLOR=#ff0000]<modifierKey>[/COLOR] [COLOR=#9966cc]<key>[/COLOR] = {[COLOR=#ff0000]$1[/COLOR]+[COLOR=#9966cc]$2[/COLOR]};
 [COLOR=#008000]<militaryKey> := [/COLOR] 
 [COLOR=#008000]  ( … Alpha =a | Bravo   =b | Charlie=c |… )[/COLOR]
 e.g.  
 say  “[COLOR=#000080]Press[/COLOR] [COLOR=#ff0000]Alt[/COLOR] [COLOR=#9966cc]echo[/COLOR] (Edit menu)
 Output: {[COLOR=#ff0000]Alt[/COLOR]+[COLOR=#9966cc]e[/COLOR]}[COLOR=#008000]a[/COLOR]
 (pause speaking)
 say  “[COLOR=#008000]alpha[/COLOR]”.
 Output: [COLOR=#008000]a[/COLOR](the access key for Select All)  
 

 Shorten the spoken part by removing the “Press” in the spoken term:
 [COLOR=#ff0000]<modifierKey>[/COLOR] [COLOR=#9966cc]<key>[/COLOR] = {[COLOR=#ff0000]$1[/COLOR]+[COLOR=#9966cc]$2[/COLOR]};
 e.g.  
 say  “[COLOR=#ff0000]Alt[/COLOR][COLOR=#9966cc]echo[/COLOR]”.
 (pause)
 say  “[COLOR=#008000]alpha[/COLOR]” .
 

 (Pause before saying “alpha”, but if you activate something called command sequences, you don't have to pause between saying commands. Dragon NaturallySpeaking does not allow you to say commands in rapid succession. Vocola and Dragonfly restore this feature)


 And to shorten it further, remove the “Alt”,  and add alternatives:
[COLOR=#666600]arpeggio=a | buoyage=b | contempo=c | drongo=d | [/COLOR][COLOR=#666600]emissary=e [/COLOR][COLOR=#666600]...[/COLOR] = {[COLOR=#0084d1]Alt[/COLOR]+[COLOR=#666600]$1[/COLOR]}[COLOR=#9966cc]a[/COLOR];
 e.g. say “[COLOR=#666600]emissary[/COLOR] [COLOR=#9966cc]alpha[/COLOR]”
 Output: {[COLOR=#0084d1]Alt[/COLOR]+[COLOR=#666600]e[/COLOR]}[COLOR=#9966cc]a[/COLOR]
 (there's more effort needed to remember the alternatives, but it gives you variety, and makes the spoken part shorter).
 

 Access keys, and the Alt modifier can possibly be more consistent and reliable (you could make it more reliable with Vocola.AddTermAlternate([COLOR=#666600]drongo[/COLOR], bongo, congo) so that a misrecognition of “bongo” and “congo” redirects, and makes it as if you said “drongo”). You are more independent of programs because if an application action isn't defined by voice, you can navigate to, and activate it by using the under-lined accelerator keys instead. You don't have to wait for a program to support select-and-say of window items. It's just another way to get people comfortable with using voice commands.
 

 **Coding by voice**

 As voice commands grow, scripts and macros become larger and more complex, and a person may spend more time using an editor, looking at code, and thinking about programming. Eventually, you may start to dabble with commands that involve inserting code:
 

 [COLOR=#000080]<modifierKey> := Shift | Control=Ctrl | Alt | Alternate=Alt | Win | Windows=Win[/COLOR];
 [COLOR=#666600]<key> := <actionKey> | <characterKey>[/COLOR];
 [COLOR=#ff3366]Insert[/COLOR] [COLOR=#000080]<modifierKey>[/COLOR] [COLOR=#666600]<key>[/COLOR] = Main.InsertText({[COLOR=#000080]$1[/COLOR]+[COLOR=#666600]$2[/COLOR]});
 e.g. say “[COLOR=#ff3366]Insert[/COLOR] [COLOR=#000080]Control[/COLOR] [COLOR=#666600]Right[/COLOR]”.
 Output: {Control+Right}
 Thisinserts the literal “{Control+Right}” keystroke specifier, which can be used in a voice command when you'reediting a Vocola file. ({Control+Right} would be on the [COLOR=#800000]“action”/right side[/COLOR]) (command = terms '=' [COLOR=#800000]actions[/COLOR] ';')
 

 [COLOR=#800000]<newInsert> := New|Insert[/COLOR];
 [COLOR=#800000]<newInsert>[/COLOR] [COLOR=#666600]Block[/COLOR] = newBlock();
 e.g. say “[COLOR=#800000]New[/COLOR] [COLOR=#666600]Block[/COLOR]”.
 

 [COLOR=#ff6633]selectLines(n) := {End}{Home}{Home}{Shift+Down_$n}[/COLOR];
 [COLOR=#198a8a]commentLines() := {Ctrl+e}c{Right_2}[/COLOR];
 [COLOR=#000080]Comment[/COLOR]  [COLOR=#00ae00]<n>[/COLOR] [COLOR=#800000][Lines][/COLOR] = [COLOR=#ff6633]selectLines($1)[/COLOR] [COLOR=#198a8a]commentLines()[/COLOR];
 e.g. say “[COLOR=#000080]Comment[/COLOR] [COLOR=#00ae00]4[/COLOR] [COLOR=#800000]Lines[/COLOR]”.
 or
 say “[COLOR=#000080]Comment[/COLOR] [COLOR=#00ae00]4[/COLOR]”, as “[COLOR=#800000]Lines[/COLOR]” is optional.
 

 I'm not familiar with VoiceCode, but if there are similarities with Vocola's code commands, then experience with Vocola and Unimacro might allow for an easier transition to VoiceCode, and increases the chances that people will try it out.
 

 (Is there such thing as a tool that can automatically replicate the manual, color-matching job of the tokens that I did?)
 

 **Counter-arguments**

 **Command-and-control vs. dictation**

 A counter-argument to the emphasis on desktop commands is that your voice will usually save you less physical touches in a command than with dictation. e.g.  
 “Show Desktop = {Win+d};” can save you two keyboard button presses (“Win” and “d”). If you wanted the literal “show desktop” put into dictation, you would be saving twelve physical inputs. You're saving less work. There is also a higher risk of voice strain if you are too excessive with voice commands.  
 

 However, “because DNS prioritizes command recognition highly, commands are seldom misrecognized and can be very concise”. If commands are supposedly less prone to misrecognition, they would be less prone to repetition.  
 

 **Casual vs. Pareto**

 A counter-argument to promoting a more approachable program (such as Vocola) can be found in the article about the Pareto principle that was posted above which talked about catering to the smaller, but high-value-creating users. A small number of people use VoiceCode, but it benefits many other people, even if they haven't heard of it.  
 

 Nevertheless, I believe that even though Vocola and Unimacro encompasses and targets more casual users, it may act as a first step to voice recognition and scripting, and be a gateway to more users trying out programs like VoiceCode. More end-users may also mean that there is a larger percentage of power users, and people that can help free-up the main developers.
 

 **User comfort**

 Once a person has taken that first comfortable step into speech recognition (frequently used) commands, has bought a decent microphone, has their headset plugged in a lot of the time, invests in some voice scripts, has delved into documentation, they might become more expansive with their use of voice recognition, and see more opportunities e.g. be able to tilt back, put their legs up, and control the computer hands-free solely by way of voice and eye-tracking. The general population, including full-fledged programmers, needs to be comfortable with the basic commands before they even begin to think about using programs like VoiceCoder.
 

 **A look to Microsoft**

 **Microsoft is a proponent of accessibility  **

 “Microsoft Announces Free Accessibility Tools and Training for Developers”
 

 “Microsoft Corp. today announced the immediate availability of Microsoft Accessibility Tools & Training, a package of free online accessibility training courses, tools and other resources to help developers worldwide create technology products, services and websites that are accessible to people with disabilities, and to enable business leaders to make more strategic technology decisions.
 Microsoft made the announcement at the 26th Annual International Technology and Persons with Disabilities Conference, sponsored by California State University, Northridge (CSUN).”.
 
Citation: Disabled World News (2011-03-17) - [http://www.disabled-world.com/disability/accessibility/websitedesign/accessibility-developers.php#ixzz2EoIZM272](http://www.disabled-world.com/disability/accessibility/websitedesign/accessibility-developers.php#ixzz2EoIZM272)
 

 **Current state of Microsoft accuracy**

 “Unfortunately, WSR's dictation is still subpar. I tried it recently and got an annoyingly large frequency of noise words being typed. This problem is apparently so bad that Rick Mohr, creator of Vocola 3, recently switched back to DNS.”.
 

 Microsoft and Chrome tests:
 I want to output the following: “I can attest to the shortcomings of Windows speech recognition”
 

 Google Chrome test results:
 I can attest to the shortcomings of when the speech recognition
 (on the first try, the correct result was just 2 items below the drop-down list of alternatives)
 I can attest to the shortcomings of Windows speech recognition (success on the second try)
 (Chrome's drop-down list of auto-complete alternatives that comes into view, even on a successful first attempt, is effective at letting you make easy and fast corrections, as it sometimes involves alternatives on multiple words in different places. I guess that's the advantage of a search query utterance only being a small chunk of text).
 

 Windows speech recognition test results:
 I didn't test the shortcomings when discrete recognition
 I can attest to the shortcomings of discrete rich nation
 And to test to the comments of windows speech recognition
 and I can attest to the shortcomings when the speicher technician
 I can attest to the shortcomings when the speaker J mission  
 I can attest to the shortcomings of windows speech recognition (Yea!)
 I can attest to the shortcomings of windows speech recognition (2 in a row!)
 I didn't test to the shortcomings of clinton's speech recognition (lost the streak)
 I can attest to this shortcomings alone of speech recognition
 I can attest to the trial Cummings wind of speech recognition
 I can attest to the shortcomings of Wendell speech recognition
 

 **Vocola 3 to Vocola 2**

 I was so bummed out to find out how incapable Windows' recognition was, and it looks like I'll be forced from Vocola 3 on Windows speech recognition, to Vocola 2 on Nuance's Dragon NaturallySpeaking.
 (The best thing I can hope for is for
 <_anything> = {PgDn};
 to at least work in Vocola 3. It should bypass the horrendous recognition because everything will now be recognized).
 

 **Price and demand**

 It's a shame because you don't get to promote a free tool. The number of users that you gain going from a 3 dollars to 2 dollars application, or a 2 dollars to 1 dollar application is a lot less than the users gained from going from a 1 dollar to free application. If someone manages to access Google voice recognition, you potentially have access to a solid, free tool again.
 

 **Lobbying Ubuntu users**

 Many justifications for support from Ubuntu users can be found in the previous “Google and Ubuntu are allies” section. Google's speech recognition would aid in leveling the playing field between Windows and Ubuntu. There are many third-party extensions and corresponding communities that currently connect to Dragon NaturallySpeaking on Windows. Even if Dragon NaturallySpeaking comes to Linux, the time waiting could be used to foster the growth of developer and user experience with Google voice recognition extensions instead.  
 

 **Nuance and Linux/Ubuntu**

 From the Nuance community forums:
 

 “What is the installed user base for Linux? How many corporate users run their desktops on Unix?  If the answer is anything less than a large number, then you might find it easier to work out why you have problems with Windows and sort those out rather than expect Nuance to change its business model.”.
 

 “Outside of commercially sensitive bespoke and specialist software, Unix remains essentially a hobbyist system, used by people who don't want to pay for their software.”.
 

 **Trends in desktop speech technologies**

 “Going forward I don't expect either [the WSR or Dragon] platform to improve”. -Rick Mohr (architect of Vocola)
 

 **Microsoft trends**

 “Since WSR is part of the operating system the opportunities for fixes / enhancements are few and far between. ”.
 

 **Nuance trends (in attitude and support)**

 “If you pause and then start dictating again, sometimes, but not always it will insert a series of invisible characters, wipe out the end of the sentence and put in a capital letter. Why? Beats the ever loving crap out of me. It's worse in gaim and chatzilla but it shows up almost everywhere. We need to find some way of getting more control over these problems because no corporation should ever have as much influence over our quality of life and ability to work as nuance does.”.
 

 “It's sad but I don't think nuance realizes that for relatively little effort, they would get positive credit that would improve their reputation and sales in other domains. The effort would need to be little more than the tools and the knowledge with maybe a little mentoring on how to build applications as well as repair and replace the systems that "don't serve our needs". And maybe, just maybe a contest to find (to some rational amount) the development of open source speech recognition applications. Not unlike the Google summer of code. But unfortunately, I'm not sure nuance recognizes the value in such an effort.”.
 

 (the last 2 comments are from way back in 2007, and from what I've read about Dragon NaturallySpeaking 12 from this thread, Nuance and its program is getting harder and harder to work with).
 

 **Google trends**

 **Android adoption  **

 [http://in.androidauthority.com/wp-content/uploads/2012/11/Android-adoption-rate-growing-steadily.jpg](http://in.androidauthority.com/wp-content/uploads/2012/11/Android-adoption-rate-growing-steadily.jpg)
 

 “Android adoption rate is growing at a healthy pace, which is also 6 times faster than that of iPhone’s adoption rate.”.
 

 [http://in.androidauthority.com/android-adoption-rate-much-faster-than-iphone-5691/](http://in.androidauthority.com/android-adoption-rate-much-faster-than-iphone-5691/)
 

 “Google's smartphone OS Android became the world's most widely used smartphone platform in just a few years after the first Android-powered phone launched and soon tablets running Google's OS are predicted to overtake Apple's iPad dominance.
 "They are planting seeds in mobile, small business, they're more proactive in voice technology, there's no question Google is spreading their wings into other technologies to field new levels of growth," Thill said. "You give bigger credit to Google for disrupting the market. They have nothing to lose. Microsoft has no record of mixing things up."”.
 [http://finance.yahoo.com/news/googles-enterprise-biz-means-microsoft-002101697.html](http://finance.yahoo.com/news/googles-enterprise-biz-means-microsoft-002101697.html)
 

 **Google and improvements in voice recognition**

 Google is probably the most likely candidate to realize the largest improvements in voice recognition:
 

 “Google brain simulator learns”
 

 “Andrew Ng, director of Stanford's Artificial Intelligence Lab, worked with Google X-Lab engineers for several years to create one of the largest artificial neural networks in the world.”.
 

 “It is leading to significant advances in areas as diverse as machine vision and perception, speech recognition and language translation.”.
 

 [http://www.cbc.ca/news/yourcommunity/2012/06/google-brain-simulator-learns-to-identify-cats-on-the-internet.html](http://www.cbc.ca/news/yourcommunity/2012/06/google-brain-simulator-learns-to-identify-cats-on-the-internet.html)
 

 **To Google, voice recognition is part of its broader ecosystem**

 “We're talking about the search engine that was built on strict automation principles: Google's code takes the long route and is more robust for it. We're talking about the global leader in AI.
 Due to the strictly automated way Google's code in AI is built, a product might take some time to get off the ground, but once it does, it can gain momentum quite quickly.”.
 “To Google, voice recognition is part of its broader ecosystem. For example: Project Glass, the next iPhone, includes voice recognition. This ecosystem strategy means Google will put a lot of resources into voice recognition, but can still offer it for free. Such "spillover" has famously diluted the pricing power of competitors like Microsoft. This situation would be similarly devastating for Nuance, especially without software patents to fall back on.”.
 

 [http://seekingalpha.com/article/927661-a-nuanced-case-against-nuance](http://seekingalpha.com/article/927661-a-nuanced-case-against-nuance)
 

 **Nuance vs. open-source**

 “The bottom line is that Nuance is not going to support this framework. In addition, if and when, and I suspect that it is just a matter of when, Nuance moves DNS from SAPI 4 to SAPI 5, you will lose the ability to use Natlink/NatPython/Vocola to interface with DNS scripting and any of the Dragon NaturallySpeaking engine commands. At that point, everything will have to be rewritten and it will have to be done independent of any help from Joel Gould by you and anyone else involved in that open source project. Nuance is not going to give you their blessing”.
 

 “I think you forget that Nuance is not in the least bit interested in supporting that which it thinks should simply go away. You folks have simply been lucky that Nuance has never decided to simply shut you down, but that is, again, largely due to the fact that you represent no threat to their bottom line at this point.
 Sorry to present such a negative perspective about the future of support for Natlink in DNS, but you folks are "dreaming of a white Christmas" that is never going to come to pass”.
 

 “the director of development used to come to the Boston voice user meetings and do presentations about the latest and greatest. In the last couple of years, he indicated that yes Nuance officially detested Natlink and asked us to please not push him on it.”.
 

 **Google and open-source**

 “Recognizing the vital role that open source software plays at Google, we of the Open Source Programs Office are tasked with maintaining a healthy relationship with the open source software development community.
 We do this by releasing Google-created code, providing vital infrastructure, supporting open source organizations, handling internal open source compliance, and by running student outreach programs such as Google Summer of Code and Google Code-in. Explore the different ways we serve the open source community through these sites on Google Code:”.
 [http://code.google.com/opensource/](http://code.google.com/opensource/)
 

 “Google encourages open source projects using the Google Apps APIs. If you have developed applications, scripts, or APIs that you would like to share with other developers and the user community, tell us about it here.”.
 [https://developers.google.com/google-apps/help/open-source](https://developers.google.com/google-apps/help/open-source)
 

 VoiceCode is (, I think,) government initiated, open source, and free, and I think most of the other tools discussed in the VoiceCode forum are predominantly non-profit also.
 

 **Google culture**

 I recently messaged a Google employee about his fantastic, open-source, educational tool: [http://www.pythontutor.com/visualize.html](http://www.pythontutor.com/visualize.html). Video: Teaching Python Programming With Web-Based Interactive Program Visualizations: [www.youtube.com/watch?v=nc1A7Ywzkpg#t=3m10s]("http://www.youtube.com/watch?v=nc1A7Ywzkpg#t=3m10s").  
 

 "Online Python Tutor ([www.pythontutor.com]("http://www.pythontutor.com")) is a free educational tool that helps students overcome a fundamental barrier to learning programming: understanding what happens as the computer executes each line of a program's source code. Using this tool, a teacher or student can write a Python program directly in the web browser and visualize what the computer is doing step-by-step as it executes the program.".
 

 "So far, over 100,000 people have used Online Python Tutor to understand and debug their programs, often as a supplement to learning from textbooks, lecture notes, and online programming tutorials.".
 

 “Free, open-source BSD-licensed code on GitHub”.
 

 He was very receptive to suggestions, and I think he's just 1 representation of Google's more responsive nature compared to other companies. They're a much larger and heterogeneous company than Nuance, with reaches in numerous fields. They're in renewable energy, and venture capital investment, they fund the Singularity University, and just this week, they “announced the disbursement of a 5 million dollar grant to the World Wildlife Fund (WWF) to purchase a fleet of drone aircrafts in Africa”.
 

 Since they're more likely to have a more broader view, they could possibly be more receptive to the points that are made in this forum.
 

 **Nuance and accessibility**

 “One other thing I could do for the group is if we came up with a coherent document of what we need, I could speak to the state senator in Massachusetts who is in nuances district, and a huge accessibility advocate since he is disabled himself and apply a little pressure there.”.  
 

 “Disabled programmers are best a drop in the ocean in terms of market share to Nuance.”. “I spoke recently to a developer who worked on the deep insides and he didn't even know Natlink existed but confirmed that Nuance really didn't care about disabled users. Everything is focused on medical and legal.”.
 

 **Google and accessibility**

 “As part of Google’s mission to make the world’s information universally accessible and useful, we’re committed to making accessibility a reality for all of our users, including those with disabilities.”.
 

 “If you have an idea to improve accessibility at Google, we want to hear it!
 We're constantly working to make our products better, and your opinions and suggestions help us do that. While we won't be able to respond to your feedback personally, we'll make sure it reaches the appropriate team. If you have multiple suggestions, please submit them separately.”.
 

 [http://www.google.com/accessibility/](http://www.google.com/accessibility/)
 

 **Google and Python**

 **Dragonfly: speech recognition framework  **

 “Dragonfly is a speech recognition framework. It is a Python package which offers a high-level object model and allows its users to easily write scripts, macros, and programs which use speech recognition.”.
 

 [http://code.google.com/p/dragonfly/](http://code.google.com/p/dragonfly/)
 

 “Dragonfly has been developed in a more modern way. It is very powerful, and integration with Unimacro and Vocola 2 will be investigated.”.
 

 “As for the interface that we use, why not use dragonfly?”. “Dragonfly works with both systems (nuance and Microsoft) which gives us more flexibility in jumping ship.”.
 

 If it's easier to get up and running, perhaps Dragonfly should be one of the first projects that is looked into being attached with Google.
 

 **Google I/O 2011: Python@Google**

 “Python is one of the key languages at Google today. It runs on many our internal systems and shows up in many of our APIs. Some of the key contributors to the language are Googlers and continue to actively promote, use, and support the language.”.
 [http://www.youtube.com/watch?v=KKQS8EDG1P4](http://www.youtube.com/watch?v=KKQS8EDG1P4)
 

 **Cost**

 Even if we have to pay (I would unquestionably pay something) to use custom voice macros with Google voice recognition, I'm pretty sure we will be paying less than 500 dollars (Dragon NaturallySpeaking Professional) per person (, and many would argue that Dragonfly, Vocola, Unimacro, and VoiceCoder are vastly more preferable to work with, yet they're free). I can't see Google charging anywhere close to that.
 

 **Developer relations with Nuance**

 “well having watched nuance go from occasionally engaged to get the complete silence, I'm not sure we could have a worse reputation/opinion of the community.”.
 

 “These are all good ideas and sadly, ideas that have been proposed by others. The problem is that nuance doesn't give a crap and sees no reason to talk. Case in point. I had a small customer that want to use the IOS SDK to use speech recognition for their app. I spent over a month trying to get someone in sales to take my call and return it. I eventually failed at this task because nuance just wasn't interested.”.
 

 “I am unfortunately of the mind that nothing short of a lawsuit will get them to pay enough attention to this problem and if we get that far, the bridge is so badly burned is no chance of cooperation”.
 

 “There right friggin cruel with their developer kit price, I personally am really considering telling Nuance to screw off”.
 

 From what I've read from the forum, it must be irritating and time-consuming to constantly find workarounds and patches, and still run the risk that “NatLink might disappear at any moment”. Even if you don't need NatLink, it's disheartening to see nonexistent support from a company, and indifference (, if not scorn).
 

 **Pessimism **

 I don't want to dissuade people from switching or abandoning, or sticking it to Nuance. Take the high ground, and continue to appeal for a relationship. The aim is just to diversify, keep options open, and have a backup plan. Anger and competition are powerful motivators, but cooperation and a reduction in duplication of efforts is always more optimal and ideal.
 

 **Cooperation and open-source are aggressive  **

 Open-source is not socialism. Because socialism goes against our natural, selfish behaviors, it has flaws. For example, there is the creation of free-loaders. This doesn't phase open-source. You've benefited from Wikipedia, but have you written a Wikipedia article? You've used Firefox, but have you submitted code to it? No? No problem. Open-source creates value that can be replicated infinitely at little to no cost due to the internet; your share is easily more than covered.  
 

 “I know there's only five or six people here that have been digging through [VoiceCode], Vocola, and Unimacro who might be willing to take this on.”. Just think about how much value 5 or 6 people are creating for everyone else.  
 

 If I make a free, public Youtube video on Vocola documentation, and 95% of people just use voice commands to surf porn faster, that's great; that's fantastic; that's inline with the pareto distribution. Every single person has the potential to be a net positive, and the incentives to contribute will only increase asthe population become more educated, knowledgeable, and productive, but I only need a few people who are excess value-creators to benefit from the productivity increase. As tools get better, it becomes harderfor anyone to not to be an excess value-creator.
 

 Don't do it for altruistic reasons; do it because open-source can be the most aggressive thing you can do.
 

 **Exponential technologies, and the advancement of society**

 I would say that open-source advances the base level of society, and someone would say, “I don't give a **** about world advancement. I only care about my own share of the pie”.  
 

 People like to discuss the percentage gain/loss in wealth and standard of living in the last decade: “For the middle-income group, the “lost decade” of the 2000s has been even worse for wealth loss than for income loss. The median income of the middle-income tier fell 5%, but median wealth (assets minus debt) declined by 28%, to $93,150 from $129,582.”. ([http://www.pewsocialtrends.org/2012/08/22/the-lost-decade-of-the-middle-class/](http://www.pewsocialtrends.org/2012/08/22/the-lost-decade-of-the-middle-class/)). A sizable amount of people say that the average person a decade ago had it better.  
 

 Most people of this generation are poorer? Let's say that you are your age now in the year 2000. What if you were twice as wealthy as today's median wealth? What about 10 times wealthier? No, I'll make you 1000 times as rich, and you're worth $93,150,000 in the year 2000. With the level of technology in the year 2000, how much would it cost you to sequence your DNA, and obtain personalized medicine? Well according to this: “Nanoscale technologies to cut DNA sequencing costs” ([http://www.kurzweilai.net/nanoscale-technologies-to-cut-dna-sequencing-costs](http://www.kurzweilai.net/nanoscale-technologies-to-cut-dna-sequencing-costs)), it looks like it's going to cost you all your money because it costs $100,000,000. How much would it cost you today? “Today, the cost of sequencing a human genome using these next-generation DNA sequencing technologies has dipped to just under $8,000.”. That would make it 12,500 times cheaper than a decade ago, and the cost drop continues, and continues to even outpace a Moore's law trend.
 

 Summary: Your money ain’t worth **** if the world doesn't advance.
 

 **Uncertainty and vulnerability of projects**

 “VoiceCode while great is slowly dying. Natlink seems to be dying faster.”. “Lets face it, if we don't make changes to VoiceCode soon, this time next year, I'll look forward to maybe seeing you guys on some other mailing list, because the only posts we'll see coming here are, "does it still work? Help!"”. “Third: My least favorite option but if everyone else's schedule is like mine these days maybe its the right choice for now, I hope not. Let it die, its had a good and productive life! R.I.P. ”.  
 

 **Plant the seeds**

 If complex commands and scripting can't work with Google, then perhaps more simpler commands, like in the Ubuntu videos above by Benoit and James, can be tried. Even if there are major flaws in the plans or implementation, and it's not currently practical to get 1 of the projects working with Google voice recognition, any kind of action and steps should be taken to establish any kind of remote connection with Google. Even if they don't acknowledge Google2Ubuntu, would the relationship be any worse than the one that currently exists with Nuance?
 

 It would be an investment, because if you're fortunate enough to get something to function, you don't have to operate in a hostile environment that continually disrupts your work, and cancels out your efforts. Google2ubuntu could provide a new speech engine that Vocola, Unimacro, VoiceCode and Dragonfly could attach to, without fear that Nuance could further raze the API.
 

 **Positive feedback loop**

 Involving more users in voice recognition instigates network externalities that benefit everyone: People send more data, increasing the accuracy for others. People buy more microphones, lowering the costs of them for others. People consume more processing power and bandwidth, lowering the costs of them for others. Also, voice scripting can be used to improve voice scripting. This all creates a positive feedback loop.  
 

 **Collaborate**

 “Understandably, power users like to hedge their bets.”. “Unimacro and Vocola ... coexist and cooperate on many aspects.”. “Integrate Vocola and Unimacro into the project so we're all working for the same thing.”.
 

 Now is as good a time as ever to put heads together, and explore new possibilities with voice recognition.  
 

 Thank you for your work, and thanks for reading.
 

 - Jeff Kang
 [https://plus.google.com/u/0/118346374063534742390/posts](https://plus.google.com/u/0/118346374063534742390/posts)
 

 (this post was made using Chrome's voice recognition in combination with Ditto clipboard manager)

```

---

### Post by bboyjkang on 2013-02-27
[SIZE=2]Ubuntu Speech Recognition enters beta before open-source release: looking for help[/SIZE]

Ubuntu Voice Recognition 

[http://www.youtube.com/watch?v=HfrQrjH3AGw](http://www.youtube.com/watch?v=HfrQrjH3AGw)
 
Private beta for Ubuntu Speech Recognition

[http://www.youtube.com/watch?v=bKeN3ehq318](http://www.youtube.com/watch?v=bKeN3ehq318)

Please include with it what you intend to do in the beta, programming, design help, etc.

Please email "ubuntuvoicerecognition at gmail dot com" to request your invite.

When spots are closed, the description will change to CLOSED. So until then, it is OPEN.

---

### Post by bboyjkang on 2013-03-18
"As promised, if I was not ready with the changes to the program by today, I would release it open source as-is. So here is the source

[https://github.com/JamezQ/ubuntu-speech-recognition](https://github.com/JamezQ/ubuntu-speech-recognition)

Look at readme.txt to get setup, feel free to ask if you have any questions.

I still plan to do my updates, but I just haven't been able to find time yet.

[#ubuntu]("https://plus.google.com/s/%23ubuntu")   [#speechrecognition]("https://plus.google.com/s/%23speechrecognition") 

EDIT: I realized that I did not specify what license the code was under. It's all GPLv3, I will update the source file headers to show this tomorrow.".

[https://plus.google.com/u/0/109027253925936825710/posts/1egSKw9BBbm](https://plus.google.com/u/0/109027253925936825710/posts/1egSKw9BBbm)

---

### Post by bboyjkang on 2013-03-18
[SIZE=3]Ubuntu Speech Recognition released on Github [/SIZE]

"As promised, if I was not ready with the changes to the program by  today, I would release it open source as-is. So here is the source

[https://github.com/JamezQ/ubuntu-speech-recognition](https://github.com/JamezQ/ubuntu-speech-recognition)

Look at readme.txt to get setup, feel free to ask if you have any questions.

I still plan to do my updates, but I just haven't been able to find time yet.

[#ubuntu]("https://plus.google.com/s/%23ubuntu")   [#speechrecognition]("https://plus.google.com/s/%23speechrecognition") 

EDIT: I realized that I did not specify what license the code was under.  It's all GPLv3, I will update the source file headers to show this  tomorrow.".

[https://plus.google.com/u/0/10902725...ts/1egSKw9BBbm]("https://plus.google.com/u/0/109027253925936825710/posts/1egSKw9BBbm")

---

