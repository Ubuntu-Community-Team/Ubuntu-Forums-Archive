---
title: "Linux SDK for eye tracking, eye interfaces, eye + speech, eye tracking advantages"
date: 2014-07-12
forum: Assistive Technology &amp; Accessibility
---

### Post by bboyjkang on 2014-07-12
(With an average reading speed, the estimated time to read this post is 1 hour)
 
[#eyetracking]("http://www.youtube.com/results?search_query=eyetracking") [#speechrecognition]("https://plus.google.com/s/%23speechrecognition") #ux #ui [#assistivetechnology]("https://plus.google.com/s/%23assistivetechnology") #accessibility #tendinosis [#disability]("http://www.youtube.com/results?search_query=disability") [#opensource]("https://plus.google.com/s/%23opensource")  &#65279;

[https://docs.google.com/document/d/1iN9lJL7cqv1xp7TwhiasJxksU8VH5BCahLEJ0eejolA/edit](https://docs.google.com/document/d/1iN9lJL7cqv1xp7TwhiasJxksU8VH5BCahLEJ0eejolA/edit)
[http://paste.ubuntu.com/7787174/](http://paste.ubuntu.com/7787174/)
 
**Eye trackers, accessibility, eye tracking interfaces, eye tracking + speech recognition together, eye tracking advantages**
 
VoiceCode “is an Open Source initiative started by the National Research Council of Canada, to develop a programming by voice toolbox.
The aim of the project is to make programming through voice input as easy and productive as with mouse and keyboard.”
 
Just like Palaver (Linux speech recognition) is an add-on for Google’s speech recognition, VoiceCode is an add-on for Dragon speech recognition.
 
I posted a message in their group about consumer-level, developer eye trackers and SDKs that are now available for preorder because some of the users have disabilities (repetitive strain injury, a.k.a. tendinosis, and a.k.a. chronic tendinitis), and I believe that eye tracking can be a technology that can help, and can assist in enhancing speech recognition.
 
The majority of them are programmers, and since some of them have a vested interest in accessibility hardware and software, I tried to see if I could nudge a couple of them to consider dabbling in eye tracking development.
 
I would like to repost the message here in the Ubuntu forums because:
 
1) Cheap commercial eye tracking coming to Linux
           
Eye Tribe has a consumer-level eye tracker that is available now for the desktop.
One of the people from Eye Tribe revealed on their forum that a Linux version of their software and SDK will be coming soon ([http://theeyetribe.com/forum/viewtopic.php?f=27&t=173&sid=21bff435fde5ecf28ed5721a35f71b86](http://theeyetribe.com/forum/viewtopic.php?f=27&t=173&sid=21bff435fde5ecf28ed5721a35f71b86)).
 
Check out the article, Weekend Project: Take a Tour of Open Source Eye-Tracking Software, on Linux.com.
You’ll see that we barely had any good options on Linux just a while ago.
 
I’m slowly trying to learn how to use Ubuntu, but I’m only able to do so because I’m using Dragon NaturallySpeaking on Windows, and eye-tracking software on Windows to navigate.
I can’t properly delve into Ubuntu until basic accessibility software gets on Ubuntu.
Now, with the upcoming release of a Linux SDK, a flood of options open up.
If there’s no support from Linux users, and Linux developers when Linux software of the eye trackers gets released, the eye-tracking company may see that it wasn’t a good gamble, and scale back their support.
(It’s only one of the eye-tracking companies that is going to release a Linux SDK, and I don’t want them to end up feeling that their efforts were in vain).
Then, the rest of the eye-tracking companies won’t bother to support Ubuntu either.
 
If Ubuntu doesn’t have accessibility options, other operating systems will continue to have an advantage.
This may not seem like a big deal, but a large portion of my post tries to explain that using eye-tracking isn’t just for accessibility reasons.
Being able to initially teleport a mouse-controlled cursor before using the mouse to finish the selection, being able to touch a “click-where-I’m-looking-at” keyboard button, and being able to use other numerous eye tracking features are things that can make anyone faster.
 
This isn’t like trying to drum up support for a popular game, and people won’t want to try Ubuntu because they can’t play their game.
Eye-tracking is going to be a very important productivity tool, and it’s going to hurt Ubuntu if supporting software isn’t there.
A significant input technology is going to fail to have accompanying software on Ubuntu, just like Nuance has decided not to bring their speech recognition to Linux.
 
2) Eye-tracking interfaces that will be built for commercial eye trackers will work with free, open source, Linux-compatible eye trackers
 
Since interfaces that work with eye tracking will start to arrive, many of them will work with the current eye-tracking systems that work on Linux.
(To assist, there is a program called Eye-Tracking Universal Driver (ETU-Driver) ([http://www.sis.uta.fi/~csolsp/projects.php](http://www.sis.uta.fi/~csolsp/projects.php)), which helps developers build tracker-independent applications).
 
If one doesn’t want a commercial eye tracker like Eye Tribe when it comes to Linux, the following projects are available:
Opengazer ([https://github.com/opengazer/OpenGazer](https://github.com/opengazer/OpenGazer)) works with Linux, and like the ITU Gaze Tracker software, which is from Eye Tribe when they were a nonprofit, it’s free software to enable a webcam to become an eye tracker.
Opengazer is open source.
Some other Linux-compatible eye trackers include eyeLike ([https://github.com/trishume/eyeLike](https://github.com/trishume/eyeLike)), a OpenCV based webcam gaze tracker based on a simple image gradient-based eye center algorithm”, and Pupil ([http://pupil-labs.com/pupil/](http://pupil-labs.com/pupil/)), an open source, mobile eye tracking hardware and software platform that started as a thesis project at MIT.
 
3) Linux head-trackers
 
Head trackers for accessibility utilize the same interfaces as eye trackers, as they both work well with larger elements.
 
2 open-source, Linux head-tracking projects are eViacam ([http://eviacam.sourceforge.net/index.php](http://eviacam.sourceforge.net/index.php)) and Mousetrap ([https://wiki.gnome.org/action/show/Projects/MouseTrap?action=show&redirect=MouseTrap](https://wiki.gnome.org/action/show/Projects/MouseTrap?action=show&redirect=MouseTrap)).
 
4) Linux touch user interfaces similar to eye-tracking interfaces
 
Fingers used for touch UIs are fatter than a mouse cursor, so touch user interfaces like Ubuntu Touch are similar to eye tracking interfaces because they both have larger elements.
 
(Beginning of post on VoiceCoder group)
 
[https://docs.google.com/document/d/1iN9lJL7cqv1xp7TwhiasJxksU8VH5BCahLEJ0eejolA/edit](https://docs.google.com/document/d/1iN9lJL7cqv1xp7TwhiasJxksU8VH5BCahLEJ0eejolA/edit)
 
This post is about eye-tracking, which has recently become affordable for consumers.
A while back, Frank Olaf Sem-jacobsen put up a thread on eye tracking: [https://groups.yahoo.com/neo/groups/VoiceCoder/conversations/topics/7223](https://groups.yahoo.com/neo/groups/VoiceCoder/conversations/topics/7223).
(Edit: I also found Anthony’s post on eye tracking: [https://groups.yahoo.com/neo/groups/VoiceCoder/conversations/topics/7695](https://groups.yahoo.com/neo/groups/VoiceCoder/conversations/topics/7695)).


Mark Lillibridge mentioned that a number of individuals in this group have disabilities, so I think eye tracking is worth another repost to update people on what’s available.
 
I would like to post this here because:
 
1) Eye-Tracking is a powerful accessibility technology
 
Eye-tracking is one of the most powerful technologies for accessibility, and can aid many people with a motor disability.
If you look at people with ALS/Lou Gehrig’s disease, they are some of the most disabled individuals.
As the neurons degenerate, and they lose control of their muscles, eye tracking is one of the few technologies that they can turn to to give them back control.
 
2) Eye-tracking can be used in varying degrees
 
Eye-Tracking can be incorporated in varying degrees to suit a user’s situation.
More disabled individuals can use more active control, such as manipulating interface objects with just your eyes.
Then there’s the more common passive control e.g. when your eye gaze approaches the bottom of a window or page of text, it automatically scrolls down (video demo: [http://youtu.be/2q9DarPET0o?t=22s](http://youtu.be/2q9DarPET0o?t=22s)).
If you were to instead press page down, your gaze most likely already went to the bottom of the window before pressing page down.
Or, you look at an interface widget to highlight it, and then press a keyboard button to select it.
Had you been using a mouse or a touchscreen, chances are that you would have looked at the widget first before moving the mouse, or touching the touchscreen to select it.
 
3) Eye-tracking interfaces can now be explored
 
I talk about types of interfaces that work with eye tracking, which are newly accessible because eye-tracking itself is recently accessible.
 
4) Eye-tracking can assist other input methods like speech recognition
 
I discuss eye tracking working in conjunction with speech recognition.
 
5) Mouse control vs. eye-tracking + mouse control (eye control to initially teleport cursor near target, and mouse to precisely place cursor)

There are features that are for using mouse control and eye control in conjunction.
E.g. Eye-tracking is used to initially teleport your cursor near your target, and then you can use the mouse to precisely place the cursor.
I discuss a research paper later on that pits mouse control by itself against “mouse control + eye-tracking teleport” in a series of computer tasks.
“Mouse control + eye-tracking teleport” ends up being the clear winner.
(If you want to skip to a demo, the authors of the paper put up a YouTube video.
2:41 shows a competition where you have to click targets as fast as possible: [http://youtu.be/7BhqRsIlROA?t=2m41s](http://youtu.be/7BhqRsIlROA?t=2m41s)).
 
6) Augmenting with eye-tracking is almost always faster – it’s not choose between “mouse + keyboard” vs. “eye tracker + keyboard”– it’s “mouse + eye-tracking teleport + keyboard” or “eye tracker + keyboard” – that is, eye-tracking is always there
 
Eye-tracking +keyboard: Eye-Tracking doesn’t have the precision of a mouse, but if an interface element and hit state is large enough, a “click-where-I’m-looking at” keyboard button will work.
 
Eye tracking + keyboard two-step process: I later talk about some eye tracking features that allow an eye controlled cursor to snap, zoom, etc. to a smaller target element, or make smaller elements project into large elements.
Sometimes it’s a two-step process, so even if you have the ability to instantly teleport the cursor, “both-hands-on-keyboard + eye-tracking two-step process” may not be suitable in certain situations.
 
Eye tracking teleport + mouse and keyboard: However, whenever you need the mouse, eye-tracking will still be there to provide an initial cursor teleport.
 
Without eye-tracking: If you have both hands on the keyboard, you lose time switching one hand to the mouse, and bringing the hand back to the keyboard.
You’re usually choosing between both hands on the keyboard, or one hand on the mouse.
 
With eye-tracking: With eye tracking, it can be used either with both hands on the keyboard (click-what-I’m-looking-at keyboard button), or one on the mouse (initial cursor teleport, then use the mouse).
You never have to forgo something to use eye-tracking; it’s always ready to make normal computer interaction faster.
 
7) Eye-tracking can make on-screen buttons , and thus macros more prevalent
 
Eye-tracking can make macros more popular because eye-tracking allows for easier activation, and thus more use of custom widgets and on-screen buttons.
A collection of custom on-screen macro buttons with recognizable, self-documenting text labels is easier to maintain than a collection of Control + Alt + Shift + <whatever> keyboard shortcuts for activating macros.
 
8) Eye-tracking is now very cheap
 
Besides the under-$100 external eye trackers that are available now, eye-tracking companies will eventually have their eye tracking components put into devices like smartphones, tablets, notebooks, and laptops, as they already have front-facing cameras, and sensors built in.
It makes the cost of additional modifications extremely low for manufacturers.
(“OEM vendors could likely add this sensor to their handsets for just five dollars” – [http://www.cnet.com/news/eye-tribe-shows-off-working-eye-tracking-on-a-mobile-phone/](http://www.cnet.com/news/eye-tribe-shows-off-working-eye-tracking-on-a-mobile-phone/)).
(“sensors are coming out that can switch between regular camera and infrared camera” – [http://www.wired.co.uk/news/archive/2014-02/25/eye-tribe-android](http://www.wired.co.uk/news/archive/2014-02/25/eye-tribe-android)).
Therefore, your next device might have eye tracking by default.
 
7) Many people aren’t aware that eye-tracking is now accessible
 
I would like to make more of the public aware of eye-tracking, as it has a lot of potential to elevate productivity.
Also, the demand from general users is the only way to progress eye-tracking for those that need it for accessibility purposes.
 
It’s a very long write-up, so a lot of it might be off-topic.
If too much of this post is irrelevant to put here, feel free to remove the post.
 
Warning: I’m not an expert of anything, and I’m not a developer, so there’s a good chance that a lot of the suggestions don’t make any sense.
 
1        **Consumer-level, developer eye trackers, and SDKs available**
2        **Eye tracking can remove physical limits**
3        **First round of eye trackers intended for developers**
4        **Eye tracking companies – Tobii and Eye Tribe**
5        **Eye-tracking (for initial warping/teleporting of cursor, and large cursor movements) + game controller (for precise cursor movements, finishing with an accurate cursor placement, and clicking)**
6        **Eye-tracking pointer motion teleport + mouse: use eye-tracking for initial warping/teleporting of cursor, and then use precision of mouse to finish selection – research paper on benefits of initially warping cursor**
        6.1 **Mouse-cursor-teleport user setting: time that mouse controlled cursor must be in rest before eye control is involved again (mouse precision still in use)**
        6.2 **Mouse-cursor-teleport user setting: point-of-gaze must be a certain distance from the mouse controlled cursor before eye control is involved again (eye-tracking is activated for larger cursor jumps)**
        6.3 **Research paper: “Mouse and Keyboard Cursor Warping to Accelerate and Reduce the Effort of Routine HCI Input Tasks – competition between mouse vs. an eye tracker + mouse to click randomly generated buttons as fast as possible”**
7        **Eye tracking working with speech recognition**
        7.1 **Adding context, and limiting the number of selection choices that a “select-what-I-say" speech command will match**
        7.2.... **Fast speech corrections with “correct-what-I’m-looking-at” button**
        7.3 **Google Earth - eye tracker to get location-based information, and speech recognition to initiate an action according to location e.g. what city is this?**
        7.4 **Commands that use both speech and eye input – e.g. select range of text lines**
                7.4.1 **Detecting interface elements – Vimium, VimFx, LabelControl, et al.**
                7.4.2........................................................ **Select range of text lines**
                7.4.3 **Advantages of eye tracking and speech in range selection command**
8        **Make eye tracking work with existing, smaller-element applications**
        8.1 **Magnification/zoom for clarification of smaller, close-together elements**
                8.1.1................................ **Magnification in eye-tracking interfaces**
                8.1.2............... **Zoom in touch interfaces e.g. Chrome on Android**
                8.1.3........................................... **E.g. of zoom in PCEye interface**
                8.1.4 **Multiple magnifications for commands that require multiple user input steps**
        8.2 **Make interface elements of existing applications responsive to gaze e.g. detecting words on a webpage**
                8.2.1............... **e.g. research paper: detecting words on a webpage**
        8.3.................................................. **Cursor snapping to interface elements**
                8.3.1...................................................................... **Dwell Clicker 2**
                8.3.2................................................................ **EyeX for Windows**
                8.3.3 **MyGaze tracker – snapping to desktop interface elements, buttons of WizKeys on-screen keyboard, and Peggle game**
        8.4 **Generate/project large-button, touch/eye-tracking UI from existing non-touch/non-eye-tracking UI**
                8.4.1 **Tag elements near point-of-gaze w/ colors, IDs, and lines – project to large elements (screenshot and mock-up)**
                8.4.2 **Only pop out alternate elements that are near point-of-gaze, instead of considering all the elements, like in Vimium**
                8.4.3 **Can have less organization, and use flow layout for projected larger elements: easier to set up, and quick eye movements can still work with disorganization (eye-controlled cursor covers distances between scattered objects quickly)**
                8.4.4 **Possibly keep generated letters/numbers/IDs of Vimium-like, element-detection programs for labeling large elements**
                8.4.5 **Generate colors to match smaller elements with larger elements – similar to semantic color highlighting in programming editors**
                8.4.6 **Displaying lines to connect smaller elements to larger elements**
                8.4.7..... **Conclusion – two-step projection process can still be fast**
                8.4.8 **E.g. DesktopEye: open-source prototype for generating eye-tracking compatible versions of window processes**
                8.4.9 **E.g. generating speech-compatible versions of open windows**
        8.5 **Conclusion – give people a sample of a potentially speedier touch/eye-tracking interface**
9        **Current interfaces, and open-source interfaces for eye-tracking**
        9.1 **Interfaces by eye tracking organizations: PCEye, EyeX, GazeMouse, GazeTalk**
                9.1.1 **Floating window, or detachable quick-access toolbar for quicker access?**
                9.1.2....................... **GazeTalk – free, predictive text entry system**
                        9.1.2.1 **Notable feature of GazeTalk: accumulate dwell time: resume dwell time after looking away**
        9.2 **Action upon slowing down, or stoppage of the cursor = eye is fixating**
                9.2.1..... **E.g. Activating widgets in GazeMouse, PCEye, and bkb**
                9.2.2 **E.g. video demonstration: slow-down upon fixation to increase cursor steadiness in a game**
                9.2.3 **E.g. Reverse cursor upon slowing down, or stoppage of the cursor (minimize overshooting) – found in video for paper, “Mouse and Keyboard Cursor Warping to Accelerate and Reduce the Effort of Routine HCI Input Tasks”**
                        9.2.3.1.............................................................. **Conclusion**
        9.3 **Other software interfaces – free head tracking software: Camera Mouse, eViacam, and Mousetrap – head-tracking interfaces similar to eye-tracking interfaces**
        9.4.......................................................................... **Open-source interfaces**
                9.4.1 **Eye-tracking Python SDK for buttons + another scripting language (AutoHotkey, AutoIt, AutoKey, PYAHK, Sikuli, etc.) for macros**
9.4.1.1        **AutoIt example – “left-click-with-magnification”**
9.4.1.2        **Automatic generation of touch/eye alternatives for smaller elements, vs. manual creation of on-screen buttons for more complex macros**
                9.4.2......................................................... **Open-Source keyboards**
                        9.4.2.1 **e.g. web-based virtual keyboard, and JavaScript framework**
                        9.4.2.2.................. **e.g. Virtual Keyboard using jQuery UI**
                9.4.3 **Alt Controller – cursor going over designed regions can launch actions – e.g. page-down or scroll-down when gaze reachs a region at the bottom**
                9.4.4 **DesktopEye: open-source prototype for switching between window processes**
                9.4.5 **Open source, eye-tracking, predictive-typing software program by Washington State University student group, Team Gleason**
                9.4.6 **bkb: open source application to control keyboard and mouse with the Tobii EyeX, The Eye Tribe gaze tracker, or an Airmouse (e.g. Leap Motion, Haptix/Touch+) – has mouse actions, virtual keyboard, and automatic scrolling**
                        9.4.6.1.............................................. **Repeating click mode**
                        9.4.6.2 **Automatically scroll down when eyes reach bottom of window**
                9.4.7 **Gazespeaker – design your own grids that have cells that launch actions, predictive keyboard, automatic scrolling, shareable grids, desktop or tablet**
                        9.4.7.1 **Work from within the program with built-in interfaces for eye-tracking e.g. custom email interface, and web browser – similar to The Grid 2, Maestro, and Vmax+ software**
                        9.4.7.2 **Customized grids with customized cells made with a visual editor (cells launch AutoHotkey, AutoKey, Autoit, PYAHK, Sikuli etc.?)**
                        9.4.7.3 **Sharing custom grids and cells – visual grids are easier to share, as opposed to sharing something like an AutoHotkey or Autoit script/text file**
                9.4.8 **Eye-Tracking Universal Driver (ETU-Driver) – independence from particular eye tracking device**
        9.5............................................................................................ **Conclusion**
10     **Google speech and accessibility**
        10.1................................................................................ **Growth of speech**
                10.1.1........................ **Taking more and more context into account**
                        10.1.1.1 **Google Research:  - “we are releasing scripts that convert a set of public data into a language model consisting of over a billion words”**
                10.1.2.................................................. **Valuing speech recognition**
                        10.1.2.1 **E.g. “Spell Up - a new word game and Chrome Experiment that helps you improve your English”**
                        10.1.2.2 **Speech recognition in Android Wear, Android Auto, and Android TV**
                10.1.3 **E.g. speech-to-text dictation is coming to the desktop version of Google Docs**
        10.2............................................................................ **Google accessibility**
11     **Eye tracking + Google speech recognition**
12     **Eye tracking potential depends on software – e.g. eye-typing**
        12.1 **Video examples of eye-typing: PCEye, JavaScript web-based virtual keyboard, bkb, and Gazespeaker**
        12.2............................................... **E.g. of fast eye-typing: Eyegaze Edge**
        12.3 **Thesis – review of the research conducted in the area of gaze-based text entry**
        12.4 **Advanced software e.g. Swype, Fleksy, SwiftKey – eye-typing with Minuum on Google Glass**
                12.4.1 **BBC video interview: Gal Sont, a programmer with ALS, creates Click2Speak, an on-screen keyboard that is powered by Swiftkey**
                12.4.2......................... **Eye-typing with Minuum on Google Glass**
                12.4.3................................................................... **Google software**
        12.5 **Touch software and UIs (and thus close-to-eye-tracking interfaces) coming to desktops, laptops, notebooks – e.g. touchscreen Windows 8 laptops, foldable Chromebook, Project Athena in Chromium, Material Design, Android apps going to Chrome OS, HTC Volantis (Flounder/Nexus 9) 8.9" tablet**
        12.6......................... **Auto-complete and auto-correct for eye-typing code**
                12.6.1 **Mirror the drop-down list of auto-complete suggestions to the on-screen keyboard**
                12.6.2 **Virtual keyboard indicator for number of drop-down list suggestions**
13     **Building eye-tracking applications by using web tools**
        13.1 **Research paper: Text 2.0 Framework: Writing Web-Based Gaze-Controlled Realtime Applications Quickly and Easily e.g. interactive reading: words disappear when you skim them**
        13.2 **Text 2.0 framework (create eye tracking apps using HTML, CSS and JavaScript) now known as gaze.io**
        13.3................................................. **Advantages of using web technology**
        13.4........................... **Tobii EyeX Chrome extension, and JavaScript API**
        13.5.......... **Pupil: web-based virtual keyboard, and JavaScript framework**
        13.6.......................................................................................... **Conclusion**
14     **Future of eye tracking**
        14.1 **Eye tracking patents, and possible, future support from larger companies**
        14.2 **OpenShades – Google Glass eye tracking – WearScript: JavaScript on Glass**
        14.3 **Augmented reality – future AR: manipulating virtual objects, disability profiles, overlay forearm with buttons (Minuum video), current AR: labeling objects (OpenShades)**
                14.3.1..... **Manipulating virtual objects, invisible disability profiles**
                14.3.2.............. **Augmented reality Minuum keyboard on forearm**
                14.3.3........................................... **OpenShades augmented reality**
15     **Advantages of eye tracking:**
        15.1...................................................................... **Already using your eyes**
        15.2.................................................................... **Comfort and ergonomics**
                15.2.1..................................................... **Vertical touchscreen pain**
        15.3 **Augmentation, not replacement – “click-where-I’m-looking-at” keyboard button, or cursor teleport before using mouse**
        15.4 **Bringing speed, recognition, and malleability of virtual buttons in a touch UI to desktop users and vertical touchscreen users that are using a non-touch UI**
                15.4.1 **e.g. Control + <whatever> = action vs. visual shortcut: button that is labeled with action**
                15.4.2 **Sharing easily learnable scripts and visual interfaces e.g. sharing Gazespeaker grids as XML files**
        15.5....................................... **Using only a keyboard for maximum speed**
                15.5.1 **Elements that are hard to access, or access quickly by keyboard**
                15.5.2 **E.g. editing code without using a mouse: “fold-the-block-of-code-that-I’m-looking-at”**
        15.6 **Mobile touch: eye-highlighting + only needing a few buttons (e.g. “single-tap-where-I’m-looking”, “double-tap-where-I’m-looking”) – hands-free scrolling – vertical mobile touchscreen – two-step process for selecting smaller elements, like text links, on non-touch-optimized websites while using mobile**
                15.6.1 **Touch gestures + “touch-where-I’m-looking” buttons vs. touch gestures alone vs. mouse-clicking on a desktop**
15.6.1.1      **Advantages of eye tracking + few function buttons: speed, comfort, and less finger and hand movement – single-taps and tablets**
                        15.6.1.2....................................... **Example apps on mobile**
                                15.6.1.2.1 **Customizing the Android Navigation Bar (easy-to-reach buttons)**
                                15.6.1.2.2 **Eye Tribe’s Android demo: tap anywhere on the screen**
                                15.6.1.2.3 **Launchers that require more than just taps i.e. swiping, double taps – replace with eye tracking + single-taps**
                                15.6.1.2.4.......... **Eye Tribe’s corner thumb buttons**
                15.6.2..... **Vertical touchscreen + “tap-where-I’m-looking” button**
                15.6.3 **Hands-free interaction: while eating, while using another computer, etc.**
                15.6.4 **Two-step process for selecting harder-to-press links and characters on non-touch-optimized (or touch-optimized) websites while using mobile**
                        15.6.4.1 **Eye-tracking two-step process for selecting a range of characters and words**
15.7       **Future: head-mounted display with eye tracking + armband, watch, ring, computer vision system, augmented reality system, etc. for input (helps work with limited space and limited gestures)**
                15.7.1 **Watches – small screen real estate works with eye-tracking**
                15.7.2............................ **Clothes: Makey Makey and OpenShades**
                15.7.3 **Computer vision recognition of forearm (Minuum video) – overlay augmented reality keys on forearm**
                15.7.4............................................................................... **Gestures**
                        15.7.4.1.............................. **While mobile: armbands, rings**
                        15.7.4.2 **While stationary: Tango, Haptix/Touch+, Leap Motion Table mode**
                                15.7.4.2.1 **Haptix/Touch+ (transform any flat surface into a 3-D multitouch surface)**
                                15.7.4.2.2 **Leap Motion Table mode (interact with surfaces) – if using air gestures without eye tracking, many more-physically-demanding gestures to memorize**
                                15.7.4.2.3.......... **Project Tango and Movidius chip**
                15.7.5........................................................................... **Conclusion**
                15.7.6................................................... **Oculus Rift + eye tracking**
                        15.7.6.1......... **Oculus Rift with the Haytham gaze tracker**
                        15.7.6.2 **Selecting and manipulating virtual objects with more speed and comfort, and less hand positions – e.g. Oculus Rift with camera for augmented reality**
                        15.7.6.3 **Navigating 20 virtual stock trading screens in Oculus Rift**
                        15.7.6.4 **Oculus Rift + eye tracking for traversal - non-gamers – “go-to-where-I’m-looking-at” e.g. eye-tracking wheelchair by researchers at Imperial College London**
16     **Conclusion**
17     **Communities**
 
**1           **Consumer-level, developer eye trackers, and SDKs available****

 
A while back, Tobii started preorders for their EyeX Controller eye tracker, and their EyeX Engine and SDK:
[https://www.youtube.com/watch?v=P8a46q6u8_s](https://www.youtube.com/watch?v=P8a46q6u8_s).
 
The price of Tobii’s package, which consists of the Tobii EyeX Controller, and the Tobii EyeX Engine and SDK, is $195.
Edit: it’s now $140.
 
Eye Tribe is another eye tracking company, and their eye tracker and software development kit is priced at $99:
[https://www.youtube.com/watch?v=2q9DarPET0o](https://www.youtube.com/watch?v=2q9DarPET0o).
 
(Eye Tribe is a spinoff of Gaze Group, a research group located at the IT University of Copenaghen).
 
**2           **Eye tracking can remove physical limits****

 
I wanted to be a more active participant in this group, but my repetitive strain injury/tendinosis (chronic tendinitis) made me lose too much hand endurance for speech recognition to make up (I’ve had laryngitis twice).
 
Hopefully, eye tracking can allow many people in the disability community to control the computer more fully.
 
**3           **First round of eye trackers intended for developers****

 
The eye trackers come with SDKs, and the first couple batches are meant for developers (it was kind of improper of me to order one for my disability, but I plan to program and develop, and the eye tracker can help out here).
 
**4           **Eye tracking companies – Tobii and Eye Tribe****

 
The Tobii EyeX Controller, and the Tobii EyeX Engine and SDK are pricier than the eye tracker from Eye Tribe, but I got both because I wanted to try both of them, and I wanted to see what kind of support would be offered for each.
But mostly, it’s because a motor disability makes obtaining these devices at these prices an absolute bargain compared to what I’d actually pay for them.
 
Some people might recall Eye Tribe when they were Gaze Group, as they created the open-source ITU GazeTracker software for use with cameras.
The software allows low-cost webcams to become eye trackers, and provides a low-cost alternative to commercial gaze tracking systems.
Lots of students and hobbyists use the software, and it helped bring the technology to many more individuals.
 
(Gaze Group is a member of the nonprofit Communication by Gaze Interaction Association (COGAIN), a European network that aims to help citizens with motor impairments communicate by “developing new technologies and systems, improving existing gaze-based interaction techniques, and facilitating the implementation of systems for everyday communication”.
 
At one time, I was about to buy a high definition webcam, and was learning how to rip out the infrared filter so that I could pair the webcam with the GazeTracker software, but Eye Tribe revealed at CES 2013 that a product would come in the next several months, so I just decided to wait.
But the open-source ITU GazeTracker software is still available for anyone that is interested: [http://www.gazegroup.org/downloads](http://www.gazegroup.org/downloads).
In the “downloads” section of Gaze Group’s website, there are already some accessibility eye-tracking applications to do some basic actions).
 
Umoove is another company that’s doing face tracking and eye-tracking, but I think you have to be selected in order to get access to a product and SDK.
 
Nevertheless, people are going to have to consider looking at all offerings.
Either way, I’m rooting for all companies to do very well.
Everyone still has to cooperate because a lot of people have yet to be aware of eye-tracking, or accept the technology as being useful.
 
**5**Eye-tracking (for initial warping/teleporting of cursor, and large cursor movements) + game controller (for precise cursor movements, finishing with an accurate cursor placement, and clicking)****

 
In the eye-tracking subreddit ([http://www.reddit.com/r/EyeTracking](http://www.reddit.com/r/EyeTracking)), there’s a video of a redditor (has some RSI) controlling the desktop, and surfing Reddit with an eye tracker and a game controller ([https://www.youtube.com/watch?v=2IjTZcbXYQY](https://www.youtube.com/watch?v=2IjTZcbXYQY)).
Eye gaze is for initial, instant, and possibly large cursor movements, and then the joystick of the controller overrides the gaze-control to offer an accurate selection of a target.
The controller buttons are for clicking.
[https://github.com/gigertron/EyeTracker](https://github.com/gigertron/EyeTracker).
 
**6**Eye-tracking pointer motion teleport + mouse: use eye-tracking for initial warping/teleporting of cursor, and then use precision of mouse to finish selection – research paper on benefits of initially warping cursor****

 
Similar to the game controller example, eye tracking can be used to initially teleport a mouse-controlled cursor near an intended target.
Once there, the mouse can override eye-control when precision is needed.


(For large interface elements like Windows 8 tiles, the mouse may not be needed to accurately place the cursor in order to finish the interaction.
You might just keep your hands on the keyboard, and use a “click-where-I’m-looking-at” keyboard button).
 
**6.1**Mouse-cursor-teleport user setting: time that mouse controlled cursor must be in rest before eye control is involved again (mouse precision still in use)****

 
Although both the developer eye trackers of Eye Tribe and Tobii are not really meant for operating the computer out-of-the-box, they both have the option to turn on a basic gaze-controlled cursor that could be potentially used with a mouse.
 
Tobii has a time setting that determines how quickly a teleport-to-point-of-gaze-upon-movement-of-mouse will occur.
You can set the time that a mouse-controlled cursor has to be still before moving the mouse will cause a teleport.
 
You can decide the amount of time that the mouse has to sit still before eye control is involved again (return of eye control could mean that either gaze controls the cursor again, or the next movement of the mouse will warp/teleport the cursor to the point-of-gaze).
It’s for, “wait, I’m still using the mouse for stability and precision.
The mouse-controlled cursor is still working in this area”.
 
**6.2**Mouse-cursor-teleport user setting: point-of-gaze must be a certain distance from the mouse controlled cursor before eye control is involved again (eye-tracking is activated for larger cursor jumps)****

 
Another setting involves deciding the distance from the mouse-controlled cursor that the point-of-gaze has to be before gaze-teleporting is involved.
It’s for, “some of the targets are close enough, so I can just use the mouse.
I’ll save eye teleporting for when the distance is large”.).
 
**6.3**Research paper: “Mouse and Keyboard Cursor Warping to Accelerate and Reduce the Effort of Routine HCI Input Tasks – competition between mouse vs. an eye tracker + mouse to click randomly generated buttons as fast as possible”****

 
A paper called “Mouse and Keyboard Cursor Warping to Accelerate and Reduce the Effort of Routine HCI Input Tasks” evaluates how initially teleporting the cursor with eye tracking in other common human computer interaction can affect the interaction.
They find that adding the teleportation clearly makes computer interaction faster.
The authors have a video demonstration here: [https://www.youtube.com/watch?v=7BhqRsIlROA](https://www.youtube.com/watch?v=7BhqRsIlROA).
A segment of the video has a scenario where “click-me” buttons are generated in random locations.
The task requires the user to click the buttons as fast as possible, and the test pits a mouse vs. an eye tracker + mouse.
You can see the performance of the eye-tracking warping + mouse at 2:41 of the video: [http://youtu.be/7BhqRsIlROA?t=2m41s](http://youtu.be/7BhqRsIlROA?t=2m41s).


Abstract: “This work explores how to use gaze tracking to aid traditional cursor positioning methods with both the mouse and the keyboard during standard human computer interaction (HCI) tasks.
The proposed approach consists of eliminating a large portion of the manual effort involved in cursor movement by warping the cursor to the estimated point of regard (PoR) of the user on the screen as estimated by video-oculography gaze tracking.
With the proposed approach, bringing the mouse cursor or the keyboard cursor to a target position on the screen still involves a manual task but the effort involved is substantially reduced in terms of mouse movement amplitude or number of keystrokes performed.
This is accomplished by the cursor warping from its original position on the screen to whatever position the user is looking at when a single keystroke or a slight mouse movement is detected.
The user adjust then the final fine-grained positioning of the cursor manually.
Requiring the user to be looking at the target position to bring the cursor there only requires marginal adaptation on the part of the user since most of the time, that is the default behavior during standard HCI.
This work has carried out an extensive user study on the effects of cursor warping in common computer tasks involving cursor repositioning.
The results show how cursor warping using gaze tracking information can speed up and reduced the physical effort required to complete several common computer tasks: mouse/trackpad target acquisition, text cursor positioning, mouse/trackpad/keyboard based text selection and drag and drop operations.
The effects of gaze tracking and cursor warping on some of these tasks have never been studied before.
The results show unequivocally that cursor warping using gaze tracking data can significantly speed up and reduce the manual effort involved in HCI for most, but not all, of the previously listed tasks.”.
 
In summary, adding eye-tracking undoubtedly speeds up computer interaction.     
 
**7           **Eye tracking working with speech recognition****

 
**7.1         **Adding context, and limiting the number of selection choices that a “select-what-I-say" speech command will match****

 
As Frank mentioned, it would be very convenient if you could use the tracker to narrow down the context to what’s near the current point-of-gaze.
You could limit the targets for speech to match, and consequently increase the accuracy of speech recognition selection.
 
**7.2**Fast speech corrections with “correct-what-I’m-looking-at” button****

 
A lot of the time, when you produce text with speech on Android, there will be a grey line underneath the text that you just produced.
It indicates that you can select it to optionally see a drop-down list of alternatives, just in case you need to correct.
Since I’m using the speech recognition on a touchscreen, it’s fast and not a bother to touch in order to do corrections.
If desired corrections appear more often in lists, touching is usually quicker than doing corrections in Dragon on a desktop.
 
If you have a vertically propped up tablet with an external keyboard, a notebook, or a laptop with an eye tracker, you could remap a keyboard button to be the “correct-what-I’m-looking-at” button, and get fast corrections on a vertical monitor.
 
**7.3**Google Earth - eye tracker to get location-based information, and speech recognition to initiate an action according to location e.g. what city is this?****

 
Olav Hermansen made a program that uses the Eye Tribe eye tracker and speech recognition to control Google Earth.
He posted a YouTube video here: [https://www.youtube.com/watch?v=zNpll95MvnE](https://www.youtube.com/watch?v=zNpll95MvnE).
This is the video description: “By combining an eye tracker and speech recognition you can rule the world.
Or at least navigate Google Earth.
The idea is to use an eye tracker to get location based information from Google Earth and use speech recognition to initiate an action accordingly to location.
By looking at Google Earth and give voice commands like "zoom in", "zoom out", "center" and "what country is this" will navigate Google Earth accordingly to where the user is looking.”.
 
[http://olavz.com/rule-the-world-with-eye-tracking-speech-recognition/](http://olavz.com/rule-the-world-with-eye-tracking-speech-recognition/).
 
**7.4         **Commands that use both speech and eye input – e.g. select range of text lines****

 
**7.4.1        **Detecting interface elements – Vimium, VimFx, LabelControl, et al.****

 
The VimFx, and Mouseless Browsing add-ons for Firefox, the Vimium extension for Chrome, the Show Numbers command for Windows speech recognition, the Show Numbers Plus application, and the LabelControl AutoHotkey script can overlay buttons, controls, and other interface elements with a number and/or letters.
You can access an interface control at any time by inputting the number and/or letter ID that belong to one of them.
(E.g. here is a GIF of the LabelControl AutoHotkey script with its numbers: i.imgur.com/INB0Jt1.gif).
(LabelControl AutoHotkey script: [http://www.donationcoder.com/Software/Skrommel/LabelControl/LabelControl.ahk](http://www.donationcoder.com/Software/Skrommel/LabelControl/LabelControl.ahk) or [http://www.donationcoder.com/Software/Skrommel/LabelControl/LabelControl.exe](http://www.donationcoder.com/Software/Skrommel/LabelControl/LabelControl.exe)).
(E.g. here is a timestamp for a video that shows the letters of Vimium: [http://youtu.be/t67Sn0RGK54?t=23s](http://youtu.be/t67Sn0RGK54?t=23s).
Here’s a picture of the letters: [http://i.imgur.com/YxRok5K.jpeg](http://i.imgur.com/YxRok5K.jpeg)).
 
**7.4.2        **Select range of text lines****

 
If numbers were bound to text lines, you could possibly have a speech command select a range of lines by saying something like, “select <number that corresponds to line that begins the selection range> <number that corresponds to line that ends the selection range>” e.g. “select 17 39”.


Let’s say that you were to do a similar selection command, but instead, you mix in eye tracking.
You could just look at the starting line, and say “select line range” to select that starting line.
Move your gaze to the line that ends the selection, and then it would select that ending line to complete the selection range, with no declaration of the numbers involved.
 
**7.4.3        **Advantages of eye tracking and speech in range selection command****

 
If you have numbers overlaying things like classes, members, lines, tokens, characters, and more in combination, packing in too many numbers could clutter your view (e.g after you say “select comma” in Dragon NaturallySpeaking, Dragon will highlight all visible instances of a comma by attaching a number to each instance: [http://i.imgur.com/VeomWwK.jpg](http://i.imgur.com/VeomWwK.jpg)).
Bringing in eye tracking can help you avoid that by not needing the numbers.


Eye input naturally takes over the highlighting step of a command.


Lastly, combining eye tracking with speech commands can let you complete commands with less use of your voice.
 
**8**Make eye tracking work with existing, smaller-element applications****

 
Touch usually has similar demands for widget sizes as eye-tracking does.
Large buttons are good for the restlessness of an eye-controlled cursor, and thicker fingers.


More and more applications will be built for eye tracking and touch.
Until then, there are some possible ways to make programs indirectly compatible with eye tracking.


**8.1         **Magnification/zoom for clarification of smaller, close-together elements****

 
**8.1.1**Magnification in eye-tracking interfaces****

 
To deal with some of the impreciseness of eye tracking, some eye tracking interfaces have a magnification feature (known as “Gaze Clarification” to some) for selecting small targets.
As you look at your intended target, a portion of the screen that includes that target becomes magnified, and the zoom level keeps increasing and increasing as you home in on your desired spot.


**8.1.2**Zoom in touch interfaces e.g. Chrome on Android****

                                                                                        
Touch interfaces have a similar feature.
When you touch multiple web elements simultaneously, perhaps due to the widgets being too small, and/or too close together, the area around where you touched pops out, giving you a magnified view of that area.
You can then clarify the interface control that you intended to touch.
Here’s a picture of magnification in Chrome on Android: ([http://i.stack.imgur.com/95nHA.png](http://i.stack.imgur.com/95nHA.png)).
 
**8.1.3**E.g. of zoom in PCEye interface****

 
You can see a demonstration of gaze clarification, and magnification at 4:22 of this video: [http://youtu.be/6n38nQQOt8U?t=4m22s](http://youtu.be/6n38nQQOt8U?t=4m22s).
 
The video shows the interface for controlling Windows for Tobii’s PCEye (I think the tracker sells for around $2000.
Thank goodness for rapidly dropping technology prices).
 
Docked to the right is a vertical menu bar (it’s kind of like the Windows 8 Charm Bar, except that I don’t think it’s context-sensitive) which has icons for actions such as left click, double-click, drag-and-drop, etc..
At the 4:22 timestamp, the user dwells and fixates on the left click icon, moves the gaze to the target, magnification begins, and then a left click is executed.
 
**8.1.4        **Multiple magnifications for commands that require multiple user input steps****

                      
So for the above “select line range” speech command that involves eye tracking, there could be a magnification and clarification before selecting the line that starts the range, and a magnification before selecting the line that will end the range.
 
To get a visual idea of this, a process that involves two separate magnifications can be found at 6:00 ([http://youtu.be/6n38nQQOt8U?t=6m](http://youtu.be/6n38nQQOt8U?t=6m)) of the PCEye video with the demonstration of drag-and-drop.
The drag-and-drop icon is first activated from the vertical menu bar on the right.
The user moves their gaze to the first target, magnification occurs, and the target is selected and picked up.
The user moves their focus to the second target, which is a folder where the first selected object will be dropped, magnification occurs, and the first target, which is a Word document, is placed into the folder.
 
**8.2         **Make interface elements of existing applications responsive to gaze e.g. detecting words on a webpage****

 
The eye tracker SDKs can be used for building new programs that are compatible with eye tracking, but I think they can also make interface controls of existing desktop and web applications react to gaze.


**8.2.1**e.g. research paper: detecting words on a webpage****

 
According to an eye tracking research paper called “The Text 2.0 Framework
Writing Web-Based Gaze-Controlled Realtime Applications Quickly and Easily” ([http://gbuscher.com/publications/BiedertBuscher10_Text20Framework.pdf](http://gbuscher.com/publications/BiedertBuscher10_Text20Framework.pdf)), there is a way to make words on webpages responsive to gaze: “Updates of the page’s general geometry are observed by a JavaScript function that tags modified DOM elements, sorts them into buckets, rechecks these buckets periodically, and batch-transmits changes back to the plugin.
The problem of word access is handled by a process we call spanification that segments text nodes consisting of multiple words into a set of span nodes containing one word each.
Using this technique we are able to obtain the bounding boxes for every word on the web page”.
 
**8.3**Cursor snapping to interface elements****

 
**8.3.1**Dwell Clicker 2****

 
There is a program called Dwell Clicker 2 ([http://sensorysoftware.com/more-assistive-tecthnology-software/dwell-clicker-2/](http://sensorysoftware.com/more-assistive-tecthnology-software/dwell-clicker-2/)).
It apparently works with a headpointer, joystick, and the Eye Tribe tracker, which was recently tested.
It “allows you to use a mouse or other pointing device without clicking buttons”.
It allows you to snap your clicks to targets.
“Target snapping is a feature that makes it easier to click on specific elements on the screen.
These elements include buttons, menu items and links.
Target snapping works by detecting elements near the pointer that you might want to click on, and locking onto the nearest element.”.


(There is a free and paid version, and I think the paid version has the snapping.)
 
Programs like this can provide a way to make an application unofficially compatible with eye tracking.
 
**8.3.2**EyeX for Windows****

 
On the Tobii forums, I read something about being able to let a “click-by-gaze snap to the nearest activatable interactor within range” in an application.
It’s possible that this is Tobii’s version of Dwell Clicker’s target snapping, and it might be found in EyeX for Windows, which is their computer control software.
 
Here is a response from the forums: “The EyeX for Windows software is designed for multi-modal use as a complement to keyboard, mouse, touchpad or other hand-based input.
We have no intent of adapting it for mono-modal use at the moment, but a third-party developer could potentially build a separate software to accomplish this, for example by using eye-based input to generate activation events for EyeX for Windows.
The precision should be enough, especially since EyeX for Windows is context-aware and can snap to clickable objects etc.”.
 
[https://www.youtube.com/watch?v=1dFSZC2a5kI](https://www.youtube.com/watch?v=1dFSZC2a5kI) apparently shows a demo of Tobii EyeX for Windows, but I don’t see any snapping to elements in that particular video.
Windows 8, with its large buttons, is used in the video, so perhaps it’s not needed.
 
**8.3.3**MyGaze tracker – snapping to desktop interface elements, buttons of WizKeys on-screen keyboard, and Peggle game****

 
SpecialEffect (a charity that helps to bring gaming to those with disabilities) has a YouTube video that exhibits the MyGaze gaze tracker (a bit more expensive at €500).
At 1:50 of the video ([http://youtu.be/2YQf_lmx_oI?t=1m50s](http://youtu.be/2YQf_lmx_oI?t=1m50s)), eye-tracking is turned on, and you can immediately see the cursor gravitate towards any interface elements that are nearby, such as desktop icons, and Windows controls.
At 2:12, a commercial on-screen keyboard called WizKeys is shown.
The cursor drifts towards the center area of keyboard buttons.
At the request of SpecialEffect, the people of MyGaze modified a game to work with eye-tracking, and Peggle was chosen.
At 5:25, you’ll see the cursor stick to close-by elements in the game.
 
**8.4**Generate/project large-button, touch/eye-tracking UI from existing non-touch/non-eye-tracking UI****

 
While trying to deal with non-eye-tracking elements, zooming and snapping might not consistently get good results, as the size and arrangement of elements can vary greatly.


To help, an additional process could involve projecting larger-sized, touch, Windows 8 Metro-like versions of non-touch/non-eye-tracking elements.
After an activation, a program would scan and detect the elements of an application (links, menus, menu items, drop-down list items, tabs et al.) that are near the point-of-gaze.
Then, the program would project larger-sized versions of those elements, while still somewhat preserving the layout.


It might operate on demand like Vimium, where you bring out the letter IDs for elements when needed, and then they disappear.
Similarly, you would bring out the alternate large-button elements, make the selection, and then continue in the regular, non-touch/non-eye-tracking interface.
 
**8.4.1**Tag elements near point-of-gaze w/ colors, IDs, and lines – project to large elements (screenshot and mock-up)****

 
Here’s a screenshot with a mock-up of the larger, colored elements that project from the smaller elements: [http://i.imgur.com/3erfG6K.png](http://i.imgur.com/3erfG6K.png).
 
**8.4.2**Only pop out alternate elements that are near point-of-gaze, instead of considering all the elements, like in Vimium****

 
Unlike Vimium, the elements that are acted upon to pop out larger elements in place could be just the ones that are near the point-of-gaze, instead of detecting everything, and putting IDs on every link.
 
**8.4.3**Can have less organization, and use flow layout for projected larger elements: easier to set up, and quick eye movements can still work with disorganization (eye-controlled cursor covers distances between scattered objects quickly)****

 
To faster set up this process, the projection program might disregard a lot of the structure and exact locations of the regular, non-touch elements of an application.
The projected, larger elements might be arranged randomly, and be packed together in a flow layout (an example of this can be seen in Gazespeaker, and eye-tracking programs that is mentioned below.
If you take its virtual keyboard, and set the positioning mode to automatic, the cells will order and position themselves to fill the available space, and cells will grow in size if other cells are deleted).
(Although, it would be better if the popped-out, larger elements somewhat mimic how the original, smaller elements are positioned relative to other smaller elements).


If it takes time to get proper organization, and one is still stuck with a disorderly arrangement of the elements, the instant movements of an eye-controlled cursor can help to handle a more cluttered interface.
 
**8.4.4**Possibly keep generated letters/numbers/IDs of Vimium-like, element-detection programs for labeling large elements****

 
It might be difficult to extract the necessary information to label the generated element.
E.g. you’re trying to project from a picture icon with no text label.
The generated letters and numbers of the element-detection programs could be useful here for automatic labeling the larger elements when they can’t be labeled.
 
You very briefly look at the character IDs that are attached to the smaller elements, and then when you pop out the larger elements, the smaller-element IDs are put on, and matched to their larger counterparts to more easily find them.
 
**8.4.5**Generate colors to match smaller elements with larger elements – similar to semantic color highlighting in programming editors****

 
The speed of this two-step selection process depends on how fast a person can track the location of projected larger elements.
In addition to IDs, the smaller elements that will be selected could be tagged with colors.
A color of a small element would be the same color as its corresponding large element.
 
The color matching would kind of be like the following code editor plug-ins that match similar tokens with the same color:
 
Color coder plug-in for Sublime: [https://github.com/vprimachenko/Sublime-Colorcoder](https://github.com/vprimachenko/Sublime-Colorcoder).
“this plugin for Sublime Text will highlight every variable in its own, consistent color — feature known as semantic highlighting, variable-name highlighting, contextual highlighting — you name it”.
([http://i.imgur.com/X4pu379.png](http://i.imgur.com/X4pu379.png)).
 
“This Atom package enables semantic highlighting for JavaScript code.
Identifiers are highlighted in different colors (the same identifier always in the same color) while everything else (like language keywords) is displayed in various shades of gray”.
([http://i.imgur.com/Ae9OH6G.png](http://i.imgur.com/Ae9OH6G.png)).
[https://atom.io/packages/language-javascript-semantic](https://atom.io/packages/language-javascript-semantic).
 
Color Identifiers mode for Emacs: [https://github.com/ankurdave/color-identifiers-mode](https://github.com/ankurdave/color-identifiers-mode).
“Color Identifiers is a minor mode for Emacs that highlights each source code identifier uniquely based on its name.”.
([http://i.imgur.com/CLQk4Ov.png](http://i.imgur.com/CLQk4Ov.png)).
 
Polychromatic for Xcode: [https://github.com/kolinkrewinkel/Polychromatic](https://github.com/kolinkrewinkel/Polychromatic).
“By giving properties, ivars, and local variables each a unique, dynamic color, and stripping away color from types which do not need it, logic becomes clear and apparent”.
([http://i.imgur.com/dHMDo34.jpg](http://i.imgur.com/dHMDo34.jpg)).
 
Recognizer for Brackets: [https://github.com/equiet/recognizer](https://github.com/equiet/recognizer).
“Experimental implementation of semantic highlighting for JavaScript development”.
 
Most of these plug-ins were inspired by a post called “Coding in color” by Evan Brooks: ([https://medium.com/programming-ideas-tutorial-and-experience/coding-in-color-3a6db2743a1e](https://medium.com/programming-ideas-tutorial-and-experience/coding-in-color-3a6db2743a1e)).
(picture of semantic highlighting in JavaScript: [http://i.imgur.com/rQDcAQB.png](http://i.imgur.com/rQDcAQB.png)).
 
Semantic highlighting has also been in the KDevelop IDE for many years.
[http://zwabel.wordpress.com/2009/01/08/c-ide-evolution-from-syntax-highlighting-to-semantic-highlighting/](http://zwabel.wordpress.com/2009/01/08/c-ide-evolution-from-syntax-highlighting-to-semantic-highlighting/).
([http://i.imgur.com/MYVeKzW.png](http://i.imgur.com/MYVeKzW.png)).
 
They make it possibly easier to quickly locate another instance of something, like a variable, so you can see where it comes from.
Colors could also make it easier to locate a popped-out element.
 
Since you may only have to detect, and project from smaller elements that are near the point-of-gaze, instead of all the elements on the screen, there would be fewer colors to generate.
This means that each color could be more distinct from other colors (I believe that another way to say this is that there is more distance between the perceptually equidistant colors), and there would be less incidents of using colors that are similar to each other, which are harder to distinguish.
 
**8.4.6**Displaying lines to connect smaller elements to larger elements****

 
Instead of using colors to match tokens, “the Racket Scheme environment performs a similar function by drawing lines from a selected token to other places where it is used”.
[http://i.imgur.com/jsoDsPG.jpg](http://i.imgur.com/jsoDsPG.jpg).


Matching smaller elements to larger elements could involve both colors and lines.
                            
**8.4.7**Conclusion – two-step projection process can still be fast****

 
A two-step pop-out process might seem slower, but with the ability to instantly eye-move the cursor before a selection, and not needing to reach for and move a mouse, the process may be faster in many instances.
Even without appropriate positioning of button projections, interacting with an eye tracker + keyboard in a crudely generated touch UI still has the potential to be faster than interacting with a mouse + keyboard in an organized, non-touch UI in certain situations.
 
**8.4.8**E.g. DesktopEye: open-source prototype for generating eye-tracking compatible versions of window processes****

 
There is an open source program on the Eye Tribe forums by Olav Hermansen: “The DesktopEye (lack of name creativity) is a prototype to easy access and changing between window processes.
It uses the eye tracker from The Eye Tribe to record eye position and trigger a menu to show when looking in the bottom left corner.
The menu will build itself from running processes present as windows on the desktop.
By looking at the menu entries, it will trigger the process to show and be brought to front.
When looking upwards and away from the menu will result in automatically closing the menu.
Eye tracking to switch between windows.
The project can be downloaded here as DesktopEye” [[http://olavz.com/wp-content/uploads/2014/02/DesktopEye.zip]](http://olavz.com/wp-content/uploads/2014/02/DesktopEye.zip]).
([https://github.com/Olavz/DesktopEye](https://github.com/Olavz/DesktopEye)).
 
Here is a picture of the windows of processes: [http://i.imgur.com/DHuhv3e.png](http://i.imgur.com/DHuhv3e.png).
The windows at the bottom that are generated from the running processes, and represent processes are large and suitable for eye tracking.).
 
**8.4.9**E.g. generating speech-compatible versions of open windows****

 
There is a speech recognition add-on for Dragon NaturallySpeaking called VoiceComputer that I tried a couple years ago.
At 0:11 of the video, [http://youtu.be/24ihD1dCK70?t=11s](http://youtu.be/24ihD1dCK70?t=11s), a user brings up a window that has a list of the open windows that are on the desktop.
The difference with the items in this list is that they have numbers attached to them.
You can use a speech recognition command with a number, such as “switch to 14”.
 
DesktopEye mirrors window processes into substitutes that work with eye tracking, and VoiceComputer mirrors open windows into variants that work with speech recognition.
 
**8.5**Conclusion – give people a sample of a potentially speedier touch/eye-tracking interface****

 
Methods like magnification, snapping, and projection of a touch/eye-tracking UI could speed up computer control, give people a glimpse of the possibilities, and create more demand for applications that have layouts that are fully designed for eye tracking and touch.
 
**9           **Current interfaces, and open-source interfaces for eye-tracking****

 
**9.1**Interfaces by eye tracking organizations: PCEye, EyeX, GazeMouse, GazeTalk****

 
I’ve read some online posts, and I believe that PCEye’s “Tobii Windows control” (can move the cursor, and click with your eyes only), and “EyeX for Windows” (move the cursor with your eyes, but use another input to click) might only be bundled with their respective eye trackers, and they will not be sold separately.
 
Gaze Group has a free gaze-based interface for simulating mouse clicks by gaze input only called GazeMouse ([http://www.gazegroup.org/downloads](http://www.gazegroup.org/downloads)).
It’s less polished, but it looks like it functions similarly to PCEye and bkb’s (eye-tracking application mentioned later) interface.


(One thing that I’ve noticed with GazeMouse is that choosing a command, like left click, means that it will be continually be repeated when the cursor stops (thinks that the user is fixating) after the cursor has been moving.
Every movement and subsequent stoppage of the cursor will produce an action until you dwell on/mouse-over a “pause” widget in a docked vertical menu bar (similar to PCEye’s bar).
On the other hand, with PCEyen and bkb’s interface, you keep going back to a widget in the vertical menu bar for each action.
 
You don’t need an eye tracker to test out GazeMouse, as you can just use your mouse to mouse-over the widgets in order to activate them.
Stopping mouse movement will simulate a fixation, and will resultantly apply the action).
 
**9.1.1**Floating window, or detachable quick-access toolbar for quicker access?****

 
The interaction on both programs might speed up if they had a movable, floating window like Paint.net’s floating “Tools” window to optionally house shortcuts of the widgets for quicker access (the gaze doesn’t have to go all the way to the edges of the screen).
 
Edit: I found an older video of what appears to be an older version of the PCEye software.
At 56 seconds in ([http://youtu.be/euBDysPgRPQ?t=56s](http://youtu.be/euBDysPgRPQ?t=56s)), you can see a floating window with 5 icons for actions.
You can pin the floating window to the edge of the screen, which shrinks it (small window with 2 small widgets).
Activating the small window from the edge brings out a full-screen version (large window with 9 large icons).
You can take the shrunken-down version of the window (2 widgets) out from the edge to make it a floating window again (5 widgets).
 
**9.1.2**GazeTalk – free, predictive text entry system****

 
GazeTalk is a free, predictive text entry system by Gaze Group: [http://wiki.cogain.org/index.php/Gazetalk_About](http://wiki.cogain.org/index.php/Gazetalk_About).
 
**9.1.2.1**Notable feature of GazeTalk: accumulate dwell time: resume dwell time after looking away****

 
If any jumpiness from eye tracking, or if a brief, voluntary withdrawal causes the fixation on an intended button to be interrupted, you could have the option to recognize a resumption of the dwelling, and continue building the dwell time for that particular button.
GazeTalk has an "Accumulate dwell time" function to “avoid the re-setting of a button”.
That is, you don’t have to start over again.
A successful activation of one button resets partial dwell time buildups in any other buttons.
(I’m you still not sure how to, or if you can transfer text out of GazeTalk to the window in focus.
With Dragon NaturallySpeaking, you can dictate into a Dictation Box, and then transfer the text.
Likewise, pressing the buttons in Windows’s on-screen keyboard transfers output to the current window in focus).
 
**9.2**Action upon slowing down, or stoppage of the cursor = eye is fixating****

 
**9.2.1**E.g. Activating widgets in GazeMouse, PCEye, and bkb****

 
In GazeMouse, bkb, and PCEye’s interface, a widget is selected as soon as the gaze slows down to a stop on that widget.


In the video, [http://youtu.be/EIGq7oV5T8A?t=2m49s](http://youtu.be/EIGq7oV5T8A?t=2m49s), a user plays a point-and-click adventure game with an eye tracker.
At 2:49 of the video, the user talks about the stream of eye tracking data that is being shown, and in that stream, there are “Gaze Data” coordinates for when the point-of-gaze is in motion, and “Fixation Data” coordinates for when the point-of-gaze is at rest.
I’m presuming that fixation might be detected when the latest and last several eye coordinates are deemed to be close together
 
**9.2.2**E.g. video demonstration: slow-down upon fixation to increase cursor steadiness in a game****

 
In another game video, the same user writes a program to detect when movement of the point-of-gaze starts to slow down into fixation, and then further slows it down to increase steadiness (at 1:08 ([http://youtu.be/_bz-4ZNs5tg?t=1m08s](http://youtu.be/_bz-4ZNs5tg?t=1m08s)), there is a “Slow Mode/Slow Zone”.
With a big change, the cursor moves quickly as usual.
If the new eye point is less than 100 pixels away, then it doesn’t go as fast; there’s a damp response.).
 
**9.2.3**E.g. Reverse cursor upon slowing down, or stoppage of the cursor (minimize overshooting) – found in video for paper, “Mouse and Keyboard Cursor Warping to Accelerate and Reduce the Effort of Routine HCI Input Tasks”****

 
The cursor movement change upon slowing down could be similar to what is talked about at 3:34 of the video for the paper, “Mouse and Keyboard Cursor Warping to Accelerate and Reduce the Effort of Routine HCI Input Tasks”: [http://youtu.be/7BhqRsIlROA?t=3m34s](http://youtu.be/7BhqRsIlROA?t=3m34s).


“To minimize overshooting of the mouse cursor when placed over the target, according to the gaze estimation area, an inertia compensation mechanism can be put in place by which instead of placing the cursor at the center of the gaze estimation area, the cursor position can be offset towards the incoming path of the manual mouse activation vector.
This technique increases the time required to perform target acquisition, but makes the cursor appear in motion toward the target after the warping occurs, which some users find convenient”.
 
**9.2.3.1**Conclusion****

 
I think these actions that occur when a cursor slows down is a way to simulate fixating on an object that’s designed to respond to eye-tracking.
I believe that a proper eye tracking interface means that the application’s objects know where the point-of-gaze is, even if it’s not necessarily near an object.
 
If you could just use mouse-hover events for fixating and dwelling, where would the eye tracking SDKs come in?
 
I’m not sure how much of the eye tracking SDKs and APIs are involved in software like GazeMouse, if any.
You can after all use GazeMouse by normally moving the mouse.
 
**9.3**Other software interfaces – free head tracking software: Camera Mouse, eViacam, and Mousetrap – head-tracking interfaces similar to eye-tracking interfaces****

 
In addition to the programs mentioned above, the nonprofit organization behind Camera Mouse, a free program for controlling the cursor with head-tracking, gives brief reviews of some of the applications that work well with it, such as Dwell Clicker 2, on their website: [http://www.cameramouse.org/downloads.html](http://www.cameramouse.org/downloads.html).
Applications like these also work well with eye trackers, as head-tracking interfaces also use large interface elements.


Two other free head-tracking programs are eViacam and Mousetrap (both are open-source, and work on Linux).
 
**9.4**Open-source interfaces****

 
I’m sure that there can be good open source interfaces for controlling the PC that function similarly to Tobii’s interfaces, Dwell Clicker 2, and GazeMouse (it’s free, but I’m not sure if its open-source).


**9.4.1**Eye-tracking Python SDK for buttons + another scripting language (AutoHotkey, AutoIt, AutoKey, PYAHK, Sikuli, etc.) for macros****

 
E.g. I’m wondering if an option to create similar widgets and interfaces is to use a GUI tool like wxpython or Qt Designer to design the buttons.
I read that Eye Tribe might have a Python SDK in the near future, and I think that there are Python API wrappers that are already available: [https://github.com/baekgaard/peyetribe](https://github.com/baekgaard/peyetribe), [https://github.com/sjobeek/pytribe](https://github.com/sjobeek/pytribe), and [https://github.com/esdalmaijer/PyTribe](https://github.com/esdalmaijer/PyTribe)).
You could then use a scripting language like AutoIt, AutoHotkey, AutoKey, PYAHK, or Sikuli to run the scripts and functions.

(AutoIt has a macro recorder called Au3Record).
 
(Sikuli uses the open-source Tesseract optical character recognition program.
Instead of writing keystrokes to access the interface elements that could be involved in macros, you just take screenshots of the interface elements.
e.g. click <screenshot of interface element>.
Here is a picture of the in-line screenshots that are used in Sikuli scripting [http://i.imgur.com/2dqGSPr.png](http://i.imgur.com/2dqGSPr.png)).


**9.4.1.1**AutoIt example – “left-click-with-magnification”****

 
E.g. Dwell on a widget with a text label of “left-click-with-magnification”, and it will activate an AutoIt script of:
 
Send("{LWIN}{+}")   ; Windows key + Plus Sign(+) is the shortcut to use the built-in zoom of Windows
MouseClick("left")
Send("{LWIN}{+}")   ; zoom back out
 
**9.4.1.2**Automatic generation of touch/eye alternatives for smaller elements, vs. manual creation of on-screen buttons for more complex macros****

 
Buttons for things like menu items could be automatically generated by other methods, like the projection concept that was mentioned above.
However, accessing common elements with a “keyboard + mouse + eye tracking cursor teleport” could be on par with “keyboard + eye tracking two-step projection process”, so using “keyboard + mouse + eye tracking cursor teleport” could be fine for a lot of the time.


Nevertheless, custom macros that are activated with keyboard + eye tracking have the potential to be the quickest.
The more complex a macro is, the more steps can be avoided.
 
Eye-tracking can make macros more commonplace because eye-tracking allows for easier activation, and thus more use of custom widgets and on-screen buttons that are usually labeled.
A collection of custom on-screen macro buttons with recognizable text labels is easier to maintain than a collection of Control + Alt + Shift + <whatever> keyboard shortcuts for activating macros.
 
**9.4.2**Open-Source keyboards****

 
From brief research, and taking keyboards as an example, there are open-source projects like Gnome, KDE, Ubuntu Linux, and Chrome OS’s on-screen keyboard/virtual keyboards.
I also noticed a few other open-source on-screen keyboards in online repositories that are written in JavaScript and Python.
 
**9.4.2.1**e.g. web-based virtual keyboard, and JavaScript framework****

Ignacio Freiberg from the eye-tracking subreddit ([http://www.reddit.com/r/EyeTracking](http://www.reddit.com/r/EyeTracking)) put up a video that demonstrates typing on a web-based virtual keyboard (great sound effects!): [https://www.youtube.com/watch?v=JoIMzfIKVDI](https://www.youtube.com/watch?v=JoIMzfIKVDI).
It is apparently powered by Pupil, an open source, mobile eye tracking hardware and software platform, and the particular keyboard is based on an open source JavaScript framework.
**9.4.2.2**e.g. Virtual Keyboard using jQuery UI****

 
jQuery on-screen virtual keyboard plugin:
 
[https://github.com/Mottie/Keyboard](https://github.com/Mottie/Keyboard)
 
Features:
 
“An on-screen virtual keyboard embedded within the browser window which will popup when a specified entry field is focused.
Autocomplete extension will integrate this keyboard plugin with jQuery UI's autocomplete widget.
Position the keyboard in any location around the element, or target another element on the page.
Easily modify the key text to any language or symbol.”.
Etc.
 
**9.4.3**Alt Controller – cursor going over designed regions can launch actions – e.g. page-down or scroll-down when gaze reachs a region at the bottom****

 
“Alt Controller is free Open Source software to help make PC games more accessible.
It lets you map computer inputs (like mouse pointer movements) to actions (like key presses) in order to create alternative controls.” [http://altcontroller.net/](http://altcontroller.net/).
 
This application works very well with less accurate eye trackers which may have more imprecision, as you can create large regions where actions occur when the mouse pointer moves inside.
 
One of the eye tracking features that has been showcased, and is already available on mobile prototypes is the ability to have a page scroll-down or page-down when the eyes approach text that is at the bottom of the page (I think this feature alone is worth more than the $5 cost to integrate an eye tracker).
Accuracy issues don’t matter as much because you can decide for yourself how big the “bottom of the window” will be.
You could simulate this with Alt Controller by defining a large horizontal rectangle at the bottom of the screen.
 
**9.4.4**DesktopEye: open-source prototype for switching between window processes****

 
As mentioned above, DesktopEye, a prototype for switching between window processes, is open source.
([https://github.com/Olavz/DesktopEye](https://github.com/Olavz/DesktopEye)).
 
**9.4.5**Open source, eye-tracking, predictive-typing software program by Washington State University student group, Team Gleason****

 
“Fifteen competing senior design teams from EECS displayed their posters in the halls of the department on April 24th.
The winning team, Team Gleason, was chosen based on their poster, their project as a whole, and their presentation.
 
Team Gleason has been developing a reliable predictive-typing software program which runs on a generic Android or Windows-8 tablet; and uses two hardware platforms for eye tracking: The Eye Tribe and The Pupil.”
 
[http://school.eecs.wsu.edu/story_team_gleason_wins_senior_design](http://school.eecs.wsu.edu/story_team_gleason_wins_senior_design)
 
“WSU’s “World Class, Face to Face” students and faculty will develop inexpensive technology and release it under open source license with no royalties”
 
[http://teamgleason.eecs.wsu.edu/](http://teamgleason.eecs.wsu.edu/)
 
“Like a smartphone’s auto-complete function, it anticipates a word or phrase based on a couple of letters.
Currently, the students are putting the software on PUPIL, a 3-D printed set of glasses that connects to a computer to translate eye movement into computer action”.
 
[http://wsm.wsu.edu/s/index.php?id=1097](http://wsm.wsu.edu/s/index.php?id=1097)
 
**9.4.6**bkb: open source application to control keyboard and mouse with the Tobii EyeX, The Eye Tribe gaze tracker, or an Airmouse (e.g. Leap Motion, Haptix/Touch+) – has mouse actions, virtual keyboard, and automatic scrolling****

 
There is an open source application that is called bkb to control a computer (by MastaLomaster).
It can be found here: [https://github.com/MastaLomaster/bkb](https://github.com/MastaLomaster/bkb)
 
The page says that the program works with the Tobii EyeX, The Eye Tribe gaze tracker, or an Airmouse (e.g. Leap Motion, Haptix/Touch+).
(There is a video demonstration on that github page: [https://www.youtube.com/watch?v=O68C4d2SNC8](https://www.youtube.com/watch?v=O68C4d2SNC8).
The video is labeled in Russian, but if you select Swahili as the closed captioning language in YouTube, you’ll get English).
 
With bkb, you dwell/fixate on widgets in a vertical menu bar that is docked on either the left or right side of your screen (there is a “switch sides” widget).
There are widgets for single clicking, double-clicking, etc..
There is also a virtual, on-screen keyboard that can be brought out.
 
It looks like bkb functions similarly to GazeMouse, and the PCEye software (although, it appears to work more comparably to the PCEye software since there is a virtual keyboard and “activate eye-scroll” widget, and you keep going back to an icon in the menu bar for each action).
 
**9.4.6.1**Repeating click mode****

 
Edit: the author says that a “repeating click” mode was added.
This was mentioned above with GazeMouse, where an action can be repeated every time that the point-of-gaze comes to a stop, and you don’t have to keep going back to a widget in the side menu bar.
 
**9.4.6.2**Automatically scroll down when eyes reach bottom of window****

 
Even though bkb is an accessibility program, it has a scroll widget that almost anyone could benefit from.
When your eyes reach the bottom of a window, the window automatically scrolls down, and vice versa.
 
**9.4.7**Gazespeaker – design your own grids that have cells that launch actions, predictive keyboard, automatic scrolling, shareable grids, desktop or tablet****

 
Gazespeaker is another open source program for controlling the computer.
 
Some of the functionalities that are listed on its website include:
 
    “display communication grids
    integrated grid visual editor
    write a text with an auto-adaptative predictive keyboard
    read web pages on the internet
    read ebooks (in html format)                                              
    read scanned books or comic strips”
 
[http://www.gazespeaker.org/features/](http://www.gazespeaker.org/features/)
 
It looks similar to the Maestro and Vmax+ software from Dynavox (makes “symbol-adapted special education software”), and The Grid 2, which is AAC (augmentative and alternative communication) software from Sensory Software (they also make Dwell Clicker 2).
 
I found the creator’s blog, and screenshots and info about the program when it was a work in progress can be found in a post from last year.
He/she mentions that ITU Gazetracker was used to test the program as it was being created.
 
**9.4.7.1**Work from within the program with built-in interfaces for eye-tracking e.g. custom email interface, and web browser – similar to The Grid 2, Maestro, and Vmax+ software****

 
It feels similar to GazeTalk, as the user works more within the program.
For example, you can enter a POP/SMTP server, and pull the data from an email service (?).
The program then provides a user with an email interface that works with eye-tracking (i.e. large buttons).
Gazespeaker can also pull websites into its own built-in web-viewer.
The browser is compatible with eye tracking, where scrolling down automatically occurs when a user’s gaze is at the bottom of a window.
 
Similarly, Gazetalk has its own email, web, and media viewer.
 
On the contrary, programs like bkb, PCEye, and GazeMouse try to assist the user in working with outside interfaces.
That is, they have features like magnification to deal with the more standard-sized elements.
 
**9.4.7.2**Customized grids with customized cells made with a visual editor (cells launch AutoHotkey, AutoKey, Autoit, PYAHK, Sikuli etc.?)****

 
One awesome feature of the program is the ability to design your own grids and cells with a visual editor.
Grids hold cells.
The software lets you define the dimensions of grids and cells, label and decorate cells, and you can have cells launch some of the predefined actions that the program provides.
 
(Perhaps in the future, the program could work with other programs like AutoHotkey, Autoit, AutoKey, PYAHK, Sikuli, etc..
In addition to launching predefined actions, the cells could launch more customized actions that can be built with the scripting programs).
 
**9.4.7.3**Sharing custom grids and cells – visual grids are easier to share, as opposed to sharing something like an AutoHotkey or Autoit script/text file****

 
On the website, it mentions that grids are stored in a standard XML file, and can be shared with other people.


I have some AutoHotkey scripts, and macros are launched by inputting keystrokes.
I wouldn’t bother to try sharing some of my scripts/text files, as I doubt anyone’s going to take the time to memorize the very personalized set of keystrokes.
 
Virtual buttons like Gazespeaker cells can have their labels customized, unlike physical keyboard buttons.

With an eye tracker, on-screen buttons like the cells are just as fast to activate as keyboard shortcuts.
You actually are touching the keyboard: look at the on-screen macro button, and then press a “click-what-I’m-looking-at” keyboard button.
 
E.g. Instead of memorizing and pressing something like Control + F6 to launch a favorite command, you could take a cell, stick and easily recognizable text label on it (could simply put the name of the command), and then activate the cell.
 
**9.4.8**Eye-Tracking Universal Driver (ETU-Driver) – independence from particular eye tracking device****

 
“Eye-Tracking Universal Driver (ETU-Driver) has been developed as a software layer to be used between actual eye tracker driver and end-user application to provide device-independent data access and control.”.
 
[http://www.sis.uta.fi/~csolsp/projects.php](http://www.sis.uta.fi/~csolsp/projects.php)
 
**9.5**Conclusion****

 
A program being open source could potentially speed up development, especially for any applications that have features like Dwell Clicker 2 or MyGaze’s element detection and target snapping, or bkb’s eye-scrolling, which any average person could benefit from.
 
It’s only now that eye tracking interfaces can really be examined because it’s only now that an eye tracker costs $100, and not a few thousand dollars.).
 
**10       **Google speech and accessibility****

 
A while back, I read about some of this group’s disappointment with Nuance’s disinterest for user groups like this one (in fairness, some of the speech extensions offer functionalities that their products deliver, except that the extensions are free, and can sometimes do much more).
I then wrote a post about how the opening of Google’s speech APIs, in combination with some burgeoning applications that allowed the creation of commands with Google’s speech, could provide some alternatives.
 
**10.1     **Growth of speech****

 
I’ll assume that Google’s speech, and its augmentative programs still meet very little of this community’s requirements.
 
However, keep in mind that only a year ago, when Palaver Speech Recognition, which is what the Google speech command program was named, was starting, it had just a few people in its Google plus community, but as of today, it has 338 members: [https://plus.google.com/communities/117295420902112738135](https://plus.google.com/communities/117295420902112738135).
 
Google speech commands are also and especially gaining popularity in the mobile arena.

“Always-listening-for-speech” mode was a major selling point in the Moto X phone.
I’ve read that spellcheck corrections are something that Google considers to be a competitive advantage, so I’m sure they value, and want to advance speech recognition, as voice samples and corrections help improve the general recognition for everyone.
 
For dictation, I see Google dictation recognition recognize some of the most obscure terms that I try to throw at it.
 
I suppose that free speech recognition on the leading search engine, and without needing a powerful local processor = more users to submit their voice samples, and correction data.
 
**10.1.1**Taking more and more context into account****

 
In a recent test of Google speech recognition, I purposely bumbled the pronunciation of, “Targaryen”, from Game of Thrones.
I get Targaryen, but I sometimes get “dark urine”, and “Tiger rant”.
If you first say “Game of Thrones”, and then follow that up with the bumbled pronunciation of the “Targaryen” speech pattern, you are much more likely to get “Targaryen”.
More uncommon words like that won’t work in Dragon NaturallySpeaking, without context, or with context.
Google most likely has much more vocabulary and context data now.
 
**10.1.1.1**Google Research:  - “we are releasing scripts that convert a set of public data into a language model consisting of over a billion words”****

 
Google Research:  - “we are releasing scripts that convert a set of public data into a language model consisting of over a billion words”
 
[http://googleresearch.blogspot.ca/2014/04/a-billion-words-because-todays-language.html](http://googleresearch.blogspot.ca/2014/04/a-billion-words-because-todays-language.html)
 
In a screenshot, a person swipes to type “New York” first: [http://i.imgur.com/8PpCkoQ.png](http://i.imgur.com/8PpCkoQ.png).


“the input patterns for “Yankees” and “takes” look very similar”.
“but in this context, the word, “New York”, is more likely to be followed by the word, “Yankees”, even though “Yankees” has a similar swipe pattern to “takes”.


**10.1.2**Valuing speech recognition****

 
“Even though Nuance has been in the voice recognition business for some time now, Google is quickly ramping up its own efforts.
Voice commands sit at the heart of Google Now, Google Glass, and the Moto X, and it has also hired renowned futurist Ray Kurzweil to work on language processing and artificial intelligence.
(Kurzweil, it’s worth noting, founded the digital imaging company that would become ScanSoft, which ended up merging with Nuance in 2005.)”
 
[http://venturebeat.com/2013/09/08/how-nuance-tapped-the-cloud-to-bring-voice-recognition-to-mobile/](http://venturebeat.com/2013/09/08/how-nuance-tapped-the-cloud-to-bring-voice-recognition-to-mobile/)
 
**10.1.2.1**E.g. “Spell Up - a new word game and Chrome Experiment that helps you improve your English”****

 
“That's the idea behind Spell Up, a new word game and Chrome Experiment that helps you improve your English using your voice—and a modern browser, of course.
It’s like a virtual spelling bee, with a twist.
 
We worked with game designers and teachers to make Spell Up both fun and educational.
The goal of the game is to correctly spell the words you hear and stack them to build the highest word tower you can—letter by letter, word by word.
The higher the tower gets, the more difficult the word challenges: You’ll be asked to pronounce words correctly, solve word jumbles and guess mystery words.
You can earn bonuses and coins to level up faster.”.
 
[http://chrome.blogspot.ca/2014/05/speak-to-learn-with-spell-up-our-latest.html](http://chrome.blogspot.ca/2014/05/speak-to-learn-with-spell-up-our-latest.html)
 
At the same time, data is being gathered to keep improving speech recognition.
 
**10.1.2.2**Speech recognition in Android Wear, Android Auto, and Android TV****

 
Edit: Android Wear, Android Auto, and Android TV were demoed at Google I/O 2014, and recognition was one of the main interfaces for all these platforms.
 
Speech recognition was significantly used in Android Wear, where a small screen of a watch isn’t suitable for typing.                                                                                    
 
**10.1.3**E.g. speech-to-text dictation is coming to the desktop version of Google Docs****

 
Marques Brownlee
Shared publicly  - 
“You saw it here first - Google Docs is getting Voice typing.&#65279;”
 
[http://www.androidpolice.com/2014/03/03/voice-to-text-dictation-is-coming-to-the-desktop-version-of-google-docs/](http://www.androidpolice.com/2014/03/03/voice-to-text-dictation-is-coming-to-the-desktop-version-of-google-docs/)
 
**10.2     **Google accessibility****

 
In my old post about Palaver, I also mentioned that Google seems to value accessibility more than Nuance.
In their latest developer conference, Google demonstrated some great open-source tools that make it easy to create accessible apps and websites, and some of them automatically fix any issues.
 
I still think Google targets the more visible disabilities, like blindness, (I know plenty of people with lower back pain, and I’m seeing a lot more people online discussing hand pain, especially with the relatively very new, and extreme pervasiveness of mobile computing.
Unfortunately, they are invisible ailments, and are harder to measure, so it doesn’t get the same awareness), but I’m sure motor and dexterity issues are on their radar, as I’ve seen posts about dexterity on Google’s accessibility Google group.
 
Google has forums where you can talk specifically about accessibility, and they actually have employees that frequent the groups.
If you look for Google I/O videos, there are talks exclusively for accessibility, presented by teams of people that work exclusively on accessibility.
Google I/O 2014 had 14 sessions on accessibility.
 
**11       **Eye tracking + Google speech recognition****

 
Then again, attitude towards accessibility doesn’t matter if the software doesn’t come near meeting the functional necessities.
In terms of speech command capabilities that are required of users here, Dragon and its extensions are still dominant (for commands, but not as much for dictation, as Google is catching up, if not starting to exceed, in dictation).
                        
However, the fact that eye tracking as an input can stand completely on its own, and Google and its technologies like speech recognition are growing rapidly means that combining the two could create an option that helps to level the playing field in an area where there are few choices.
 
(I had a bad experience with the accuracy of Windows speech recognition for dictation on Windows 7, but if it has improved on Windows 8, then eye tracking with Windows speech recognition could also be a viable combo).
 
**12       **Eye tracking potential depends on software – e.g. eye-typing****

 
Eye tracking is able to be the sole input, but if you take an activity like typing words, I’ve seen that some of the methods of eye-typing on a virtual/soft keyboard can be slower, as you have to dwell on each letter for a certain amount of time.
 
For example, if you want to produce the word, “testing”, and you fixed the dwell time necessary for activation at 0.6 second, you would stare at the letter “T” for 0.6 second, stare at the letter “E” for 0.6 second, and so on, and so forth.
Although, a lot of the eye-tracking input software have predicted words that become available for you to auto complete or auto correct, and they really speed things up.
 
**12.1**Video examples of eye-typing: PCEye, JavaScript web-based virtual keyboard, bkb, and Gazespeaker****

 
Examples of eye-typing can be seen at 5:26 of the PCEye video: [http://youtu.be/6n38nQQOt8U?t=5m26s](http://youtu.be/6n38nQQOt8U?t=5m26s), or, again, in Ignacio Freiberg’s video of a web-based virtual keyboard: [https://www.youtube.com/watch?v=JoIMzfIKVDI](https://www.youtube.com/watch?v=JoIMzfIKVDI).
Bkb ([http://youtu.be/O68C4d2SNC8?t=1m20s](http://youtu.be/O68C4d2SNC8?t=1m20s)) and Gazespeaker ([http://youtu.be/03w7eIu6rY8?t=1m17s](http://youtu.be/03w7eIu6rY8?t=1m17s)) also have virtual keyboards.
 
**12.2**E.g. of fast eye-typing: Eyegaze Edge****

 
Edit: someone recently posted a YouTube link, and actually, eye-typing can be pretty fast already (Eyegaze Edge): [http://youtu.be/lY22CZ7XP-4?t=42s](http://youtu.be/lY22CZ7XP-4?t=42s)
 
**12.3**Thesis – review of the research conducted in the area of gaze-based text entry****

 
For more information about eye-tracking text entry, you can check out the thesis, “Text Entry by Eye Gaze” by Päivi Majaranta.
The “thesis provides an extensive review of the research conducted in the area of gaze-based text entry.
It summarizes results from several experiments that study various aspects of text entry by gaze.”: [https://tampub.uta.fi/handle/10024/66483](https://tampub.uta.fi/handle/10024/66483)
 
**12.4     **Advanced software e.g. Swype, Fleksy, SwiftKey – eye-typing with Minuum on Google Glass****

 
Depending on the software, eye-typing could be greatly hastened.
If you could grab an application like Swype, which allows you to speedily bounce from letter to letter without stopping, snatch applications like Fleksy and SwiftKey, which allow you to type without looking at the keyboard because they have immensely proficient word-prediction and auto-complete, and combine them with eye-tracking, then a feature like eye-typing, which currently isn’t even meant for the mainstream population, might not be so slow anymore.
 
**12.4.1**BBC video interview: Gal Sont, a programmer with ALS, creates Click2Speak, an on-screen keyboard that is powered by Swiftkey****

Gal Sont is a programmer that was diagnosed with ALS in 2009.
He created Click2Speak, an on-screen keyboard that is powered by Swiftkey.
[http://www.bbc.co.uk/programmes/p021r01n](http://www.bbc.co.uk/programmes/p021r01n)
[https://www.youtube.com/watch?v=WWMsPpBRV3A](https://www.youtube.com/watch?v=WWMsPpBRV3A)
 
Features:
 
    Works with all standard Microsoft Windows applications.
    Includes Swiftkey’s powerful features like the award-winning prediction engine, and 'Flow'.
    Supports more than 60 languages.
    Floats over other applications.
    Includes advanced visual and audio features.
    Auto-spacing and auto-capitalization.
    Choose between different layouts and sizing options.
    Contains Dwell feature that allows you to imitate a mouse click by hovering.
 
“After being diagnosed with the disease, I contacted other individuals who suffer from ALS at different stages, and began to learn about the different challenges that I would face as my disease progressed.
I also learned about the tech solutions they used to cope with these challenges.
The most basic challenge was typing, which is done using a virtual on screen keyboard, a common solution shared by not only individuals affected by ALS, but a variety of illnesses such as brain trauma, MS and spinal cord injuries victims.
The fully featured advanced on screen keyboards, again proved relatively very expensive (starting at $250), so I decided to develop the ultimate on screen keyboard on my own.
Through the development process, my own physical condition continued to deteriorate and I reached the point of needing to use these cameras and on screen keyboards myself.
I started with Microsoft’s 'ease of access’ keyboard that comes with windows.
This is an acceptable keyboard and it has a reasonable prediction engine.


For my own development needs I purchased the developer version of TOBII’s eye gaze camera.
This allowed me to code (with my eyes!) additional important features that were lacking in the Microsoft keyboard for eye control such as highlighted keys, virtual keys, auto scroll, right click, drag and much more.
 
It quickly became apparent that using our 'powered by Swiftkey’ keyboard enabled me to work faster and more accurately.
Friends who used other solutions prior to ours (not necessarily Microsoft’s) were delighted with the results, albeit a small sample size.


This started a new journey that introduced me to Swiftkey’s revolutionary technologies and how we customize them to our specific needs.
I reached a first version of our keyboard and distributed it to friends who also suffer from ALS.
They gave us invaluable feedback through the development process, and they all raved about its time saving capabilities and accuracy and how it makes their lives a little easier.
Even Swiftkey’s 'Flow’ feature is translated successfully to this environment; basically, it replaces the finger when using Swiftkey on an Android device with an eye/head/leg when using a PC/Tablet/laptop + camera/other input device + our Swiftkey powered keyboard installed.
 
At this point I had my good friend Dan join me in this endeavor as I needed help with detail design, quality assurance, market research, project management, and many other tasks.
We formed 'Click2Speak’, and we plan to make the world a better place! ...”.
 
[http://www.click2speak.net/](http://www.click2speak.net/)
 
**12.4.2**Eye-typing with Minuum on Google Glass****

 
Minuum is a one line keyboard for android smartphones (also has strong auto-correction), and the team behind it released a concept video that showed various ways of typing on Google Glass.
One method combined their virtual keyboard, and an eye tracker on the head-mounted device.
[http://youtu.be/AjcHzO3-QEg?t=46s](http://youtu.be/AjcHzO3-QEg?t=46s).
 
**12.4.3    **Google software****

 
After the Android 4.4 KitKat update, and you can now swipe the space bar between swiping words in the stock Google keyboard.
This allows you to keep the gesture and flow going without letting go of the screen, which is apparently similar to the “Flow through Space” feature that SwiftKey has.
Android 4.4’s auto-correction is also extraordinarily good.
 
I’m sure that one can incorporate eye tracking interfaces with high-level APIs, such as perhaps using eye-typing with Google Docs’ semantic and spelling suggestions, just like Palaver utilized Google’s speech APIs.
 
Recently, Google launched an add-on store for Docs and Sheets, which will potentially give people access to a large collection of third-party tools, just like the Play store.
 
Many Google APIs are free, and they keep adding features that were once less accessible, like the newly released speech recognition for Google Docs, so the standard is continually being raised.
 
**12.5**Touch software and UIs (and thus close-to-eye-tracking interfaces) coming to desktops, laptops, notebooks – e.g. touchscreen Windows 8 laptops, foldable Chromebook, Project Athena in Chromium, Material Design, Android apps going to Chrome OS, HTC Volantis (Flounder/Nexus 9) 8.9" tablet****

 
The above mobile typing applications, and other touch-based applications will most likely come to the desktop, and will bring with them their larger, more-compatible-with-eye-tracking elements.
 
These applications could come through the digital distribution platforms that are on the desktop, such as the Chrome Web Store (the “For Your Desktop” section of the Chrome Web Store hold apps that run offline and outside the browser, and are known as Chrome Apps), as the number of notebooks with touch screens keeps rising (NPD DisplaySearch Quarterly Mobile PC Shipment and Forecast Report).
 
Foldable Chromebook


There are more touch/non-touch hybrid devices, such as the Lenovo ThinkPad Yoga 11e Chromebook, which folds 360° for tablet mode.
Lenovo’s N20p Chromebook flexes to 300° (laptop mode to standing mode).
 
Project Athena

There is a new window manager for Chromium called Project Athena, and it hints to more touch interaction on Chrome OS.
 
Android apps going to Chrome OS
 
Google announced at I/O that Android apps will be coming to Chrome OS.
 
Material Design
 
Material Design is a new design language that was introduced at Google I/O 2014 for achieving consistency across devices.
Instead of a design language that is just for Android phones and tablets, it will be for the web, Chrome OS, and other devices.
              
Android L 5.0

Android L 5.0 will make use of Material Design.
 
The new multitasking feature in Android L hints at a multi-window system. It is built on Chromium and has the same look as the windowing system on Chrome OS.
 
HTC Volantis (Flounder/Nexus 9) 8.9" tablet
 
I believe that eye tracking provides more benefits when it’s applied to a vertical touchscreen (e.g. ergonomic benefits), but I don’t believe that most people are using a vertically-set up Android device for heavy work.
 
The specs on the tablet (Tegra K1 64-bit) are powerful enough to handle Chrome OS.

Android Police reports that Volantis may come with official accessories like a keyboard case ([http://www.androidpolice.com/2014/06/21/this-is-volantis-htcs-nine-inch-nexus-tablet/](http://www.androidpolice.com/2014/06/21/this-is-volantis-htcs-nine-inch-nexus-tablet/)), and keyboards are currently and mainly used for Chrome OS, not Android.

It has a more narrow 4:3 aspect ratio, which is more suitable for general work (reading, writing, browsing, programming, image editing, etc.).
This is opposed to a wider 16:9 aspect ratio, which is more suitable for watching videos.
(In the "Google I/O 2013 - Cognitive Science and Design" talk, the speaker says that experiments show that people can be faster with reading longer lines, but a lot of people prefer, and are more comfortable with reading shorter and more narrow lines: [http://youtu.be/z2exxj4COhU?t=23m29s](http://youtu.be/z2exxj4COhU?t=23m29s).
Dyson and Kipping (1997), Dyson and Haselgrove (2001), Bernard, Fernandez, and Hull (2002), Ling and van Schaik (2006). samnabi/com.
I’m sort of making that happen in this post with my text replacement of “period” “space” with “period” “manual line break”, which puts each sentence on a new line, and shortens a lot of lines).

Perhaps Volantis could be a device that functions in a hybrid fashion like the Microsoft Surface.
 
These mentioned changes show that another touch/eye-tracking interface (Android) will make its way to a more work-oriented PC (Chrome OS device), and eye-tracking would see more usage.
On the other end, touch devices (e.g. Volantis tablet) with their touch UI will see more uses for productivity, as these devices add more power, and features like multitasking.
Also, when you use a computer for productivity, you’re more likely to use a vertical screen, and eye-tracking is more valuable when the screen is upright.
(Although, eye-tracking just for teleporting a mouse controlled cursor would still be advantageous for the typical non-touch, smaller-element-interface, work-oriented PC, so an eye tracker should still find a route into a work-oriented device regardless).
 
Air-swiping with the Nod ring
 
There is a YouTube video of a gesture ring that is called the Nod.
It shows a person watching TV, and he air-swipes to produce a search term on Netflix: [http://youtu.be/dy-Ac9X9oSo?t=6s](http://youtu.be/dy-Ac9X9oSo?t=6s).
 
Rise of touchscreens for Windows 8, and rise of touchscreen laptops
 
“But they're taking off fast: in the US, touchscreen models account for a quarter of current Windows 8 laptop sales, says NPD, and Windows 8 boss Julie Larson-Green has said she expects virtually all laptops to have touchscreens soon.”
 
[http://www.theguardian.com/technology/2013/apr/09/windows-8-touchscreen-laptops-pain](http://www.theguardian.com/technology/2013/apr/09/windows-8-touchscreen-laptops-pain)
 
**12.6**Auto-complete and auto-correct for eye-typing code****

 
I read that some people on the VoiceCoder forums don’t actually use much of the speech recognition extensions for programming ([https://groups.yahoo.com/neo/groups/VoiceCoder/conversations/topics/7781](https://groups.yahoo.com/neo/groups/VoiceCoder/conversations/topics/7781)).
Instead, speech recognition is for producing characters, and the auto complete of IDEs do most of the work.
 
**12.6.1**Mirror the drop-down list of auto-complete suggestions to the on-screen keyboard****

 
If an eye tracking on-screen keyboard were to be used in an IDE, then hopefully, there’s a way to detect any drop-down list of code completion choices that appear after you start typing, and have the suggestions be mirrored to a location that is close to the keyboard.
It could be similar to the location of predicted natural language words in numerous keyboards, like Gazespeaker’s virtual keyboard, Windows’ on-screen keyboard, and Android’s stock keyboard, which usually place predictions on top of the keyboard.
(Suggestions that appear even closer to your view can be seen when you swipe with the Android keyboard.
Floating, continuously-building predicted words appear right on the letters that you swipe).
 
**12.6.2**Virtual keyboard indicator for number of drop-down list suggestions****

 
If one can’t mirror the drop-down list items to the virtual keyboard, perhaps there can be an indicator near the virtual keyboard instead.
Any open drop-down lists, and their items are detected, and the indicator displays a number that represents the amount of suggestions/drop-down list items that are currently available.
It could assist the user in deciding when to put focus back on the combo box.
As characters are typed, the number of suggestions would narrow down, and the indicator number would get smaller.
When the number of suggestions is low enough, a user could activate a virtual keyboard button that switches the view and focus to a drop-down list.
It could then be followed by a large-element, color projection (mentioned above) of the drop-down list of choices.
 
**13       **Building eye-tracking applications by using web tools****

 
**13.1**Research paper: Text 2.0 Framework: Writing Web-Based Gaze-Controlled Realtime Applications Quickly and Easily e.g. interactive reading: words disappear when you skim them****

 
There is an eye tracking research paper called “The Text 2.0 Framework
Writing Web-Based Gaze-Controlled Realtime Applications Quickly and Easily” ([http://gbuscher.com/publications/BiedertBuscher10_Text20Framework.pdf](http://gbuscher.com/publications/BiedertBuscher10_Text20Framework.pdf)), which I briefly mentioned above.


Abstract: “A plugin enables any compatible browser to interpret a new set of gaze handlers that behave similar to existing HTML and JavaScript mouse and keyboard event facilities.
Keywords like onFixation, onGazeOver, and onRead can be attached to parts of the DOM tree and are triggered on the corresponding viewing behavior.
Using this frame-work we implemented a number of applications providing help on comprehension difficulties.”.
 
From what I understand, the researchers built some applications that use eye tracking to make reading interactive.
One of the features involves the program detecting that you’re skimming past words, so those words will fade out.


In order to make the various reading comprehension programs, they created a “simple-to-use [, now open-source,] framework to construct gaze-responsive applications using web technology”.
[https://code.google.com/p/text20/](https://code.google.com/p/text20/).
 
**13.2**Text 2.0 framework (create eye tracking apps using HTML, CSS and JavaScript) now known as gaze.io****

 
The Text 2.0 framework is now known as gaze.io.
[http://gaze.io/](http://gaze.io/)
 
[https://github.com/gazeio](https://github.com/gazeio)
 
“Create stunning cross platform eye tracking apps, and it supports both interaction and analysis.
In runs on Chrome, Firefox, Internet Explorer 10+ and Safari, on Windows, Mac OS and Linux, given the eye tracker runs on said platform and has an open API”.
 
**13.3**Advantages of using web technology****

 
(From the research paper:)
 
“HTML, JavaScript and CSS are simple to use and there is a plethora of existing literature covering almost any aspect of these technologies.
That way it is also easier to properly polish an application to get an even more realistic use case than with only partially written prototypes.
 
Also, the usage of common languages and concepts significantly lowers the barrier for beginners to write eye tracking applications.
Masses of web designers are now easily capable of writing gaze-responsive applications.


Most parts of the application’s interface and reactions have been written by students familiar with web design, but not with eye tracking.
We think this fact nicely illustrates the potential of our easy-to-use eye tracking framework.
 
The API can be understood by any web designer with a bit of JavaScript experience intuitively.
Simple gaze-responsive applications can be implemented with almost no programming while complex projects benefit from a clear separation of structure (HTML), logic (JavaScript) and design (CSS).
We think the principal choice of using a browser plugin offers fundamental benefits in the long term.
The speed of the development progress in the web community is high and new exciting features are constantly integrated into browsers, enhancing the possibilities of gaze-responsive applications almost for free, as we showed with the implementation of a gaze enhanced tab exposé which we developed in only a few hours.”.
 
**13.4**Tobii EyeX Chrome extension, and JavaScript API****

 
Tobii has an extension that enables you to use Tobii EyeX in Chrome: [https://chrome.google.com/webstore/detail/tobii-eyex/ondpdhamlelacohaomibljcnnnaipmob/details?hl=en](https://chrome.google.com/webstore/detail/tobii-eyex/ondpdhamlelacohaomibljcnnnaipmob/details?hl=en).
They say that the Chrome extension accesses the EyeX Engine via JavaScript, but is, at the moment, using an internal protocol/API on top of EyeX for Windows.
They plan to add official JavaScript support, and a JavaScript API quite soon.
 
**13.5**Pupil: web-based virtual keyboard, and JavaScript framework****

 
As mentioned above, Ignacio Freiberg from the eye-tracking subreddit ([http://www.reddit.com/r/EyeTracking](http://www.reddit.com/r/EyeTracking)) put up a video that demonstrates typing on a web-based virtual keyboard that is based on an open source JavaScript framework.
 
“Hello everyone!
 
Imagine you can create web apps using HTML+CSS+Javascript, that can be controlled with Pupil.
 
Well, I've just built a first prototype (a virtual keyboard).
 
My short term plan is to build some more apps to show the potential of this, which is huge.


For example, with a few improvements the virtual keyboard could be extremely more effective (predictive text, error correction mechanisms, machine learning).
Many other apps could be *easily* created on this context, including speed reading, social network interfaces, marketing analysis apps, and others.
 
My long term plan is to build a nice, clean Javascript framework to let people build their own apps.
Just imagine you could add this to your web apps:
$(".myButton").sightOver(function() { });
 
Comments? Ideas?”.
 
[https://groups.google.com/forum/#!msg/pupil-discuss/21EqMal5-Ig/MZJn_7p1_OsJ](https://groups.google.com/forum/#!msg/pupil-discuss/21EqMal5-Ig/MZJn_7p1_OsJ)
 
**13.6**Conclusion****

 
Programs and tools built with web technologies are improving at a very fast pace.
 
E.g. Chrome Apps (uses Cordova), which can be written in HTML, JavaScript and CSS, are coming to Android and iOS.
By using possibly easier programming languages, and needing just one code base for a simpler porting process, web tools are becoming more popular and enticing to use.
 
The Text 2.0 framework/gaze.io demonstrates that eye tracking is already ready to work with web technologies, which should help eye tracking expand.
 
**14       **Future of eye tracking****

 
**14.1     **Eye tracking patents, and possible, future support from larger companies****

 
Notably, Google has an eye tracking patent that involves recording advertisement impressions through eye focus with pay-per-gaze, and another patent that demonstrates a method to unlock a device by having a sensor in a head-mounted accessory (probably something like Google Glass) track the patterns of the pupil.
([http://www.engadget.com/2012/08/07/google-patent-for-eye-tracking-based-unlock-system/](http://www.engadget.com/2012/08/07/google-patent-for-eye-tracking-based-unlock-system/))( [http://www.wired.com/2013/09/how-googles-pay-per-gaze-patent-paves-the-way-for-wearable-ad-tech/](http://www.wired.com/2013/09/how-googles-pay-per-gaze-patent-paves-the-way-for-wearable-ad-tech/))
 
Apple filed an eye tracking patent that deals with something called Troxler fading: “One result of this phenomenon is the perceived fading of a fixated stimulus when its retinal image is made stationary on the retina, which is otherwise known as a stabilized retinal image.”.
“Apple provides systems, methods, and devices that provide a user of a GUI with one or more measures to counteract a perceptual fading of a cursor with respect to the GUI.” ([http://www.patentlyapple.com/patently-apple/2013/10/apple-files-eye-tracking-system-with-advanced-gaze-controls.html](http://www.patentlyapple.com/patently-apple/2013/10/apple-files-eye-tracking-system-with-advanced-gaze-controls.html))
 
Also, Nokia has a patent for a future head-mounted device: “The patent explains that there will be two cameras on the wearable device, one which will track the gaze of an eye to help position the cursor on the screen.
The other camera will focus on hand gestures, which will allow users to select an item on a menu.
According to the patent, these gestures could be the shaking of a palm or the movement of a fist.
The first camera could be an infrared camera focused on one eye of the user of the NED.
The second camera would probably be a "so called side down-looking camera observing gestures of the hand."”.
([http://www.phonearena.com/news/Nokia-receives-eye-tracking-patent-for-its-own-connected-specs_id53956](http://www.phonearena.com/news/Nokia-receives-eye-tracking-patent-for-its-own-connected-specs_id53956)).
 
In indicates that eye tracking should have even more backing in the near future.
 
**14.2     **OpenShades – Google Glass eye tracking – WearScript: JavaScript on Glass****

 
People in the community, OpenShades, have already added eye-tracking to Google glass by adapting from Pupil, an open source eye tracking hardware and software platform that started as a thesis project at MIT.
OpenShades’ objectives include computer vision and recognition, augmented reality, and accessibility.
[http://www.openshades.com/](http://www.openshades.com/).
 
Just like the people behind the “Text 2.0 Framework: Writing Web-Based Gaze-Controlled Realtime Applications Quickly and Easily” paper saw the benefits of utilizing web technology with eye tracking, the people of OpenShades have also acknowledged the advantages of web tools, and developed WearScript: “WearScript is a library that allows you to execute Javascript on Glass that can interact with the underlying device.
WearScript combines the power of Android development on Glass with the learning curve of a website.
Go from concept to demo in a fraction of the time.”.
 
**14.3     **Augmented reality – future AR: manipulating virtual objects, disability profiles, overlay forearm with buttons (Minuum video), current AR: labeling objects (OpenShades)****

 
**14.3.1**Manipulating virtual objects, invisible disability profiles****

 
At 13:30 of a video of Eye Tribe’s presentation at Techcrunch’s Hardware Battlefield ([http://techcrunch.com/video/hardware-battlefield-ces-2014-the-eye-tribe/518078469/](http://techcrunch.com/video/hardware-battlefield-ces-2014-the-eye-tribe/518078469/)), cofounder Sune Johansen pitches a future application of augmented reality in glasses to Martha Stewart and the rest of the judges.
You could use your eyes to manipulate the augmented reality projections.
Another example is where a sensor detects that you’re looking at a person, and an online profile pops up.
This could help people with invisible disabilities broadcast their status.
 
**14.3.2**Augmented reality Minuum keyboard on forearm****

 
The Minuum video demonstrates computer vision on Glass recognizing a user’s forearm, and an augmented reality system overlaying the forearm with a Minuum keyboard.
The virtual buttons don’t have to show up until the eye tracking system recognizes that the user is looking at the forearms.
([http://youtu.be/AjcHzO3-QEg?t=46s](http://youtu.be/AjcHzO3-QEg?t=46s)).
 
**14.3.3**OpenShades augmented reality****

 
The people of OpenShades showcase a budding example of augmented reality at 2:45 of a video: [http://youtu.be/pHCwaaactyY?t=2m45s](http://youtu.be/pHCwaaactyY?t=2m45s) – “Interactive Augmented Reality using Google Glass”.
 
A person walks around a lunar landing display in a museum.
When he looks at the Buzz Aldrin and Neil Armstrong manikins, their names are rectified on the screen of the device.
 
Another augmented reality example from OpenShades can be found at 7:55 of their video, “WearScript: Myo/Pebble/Magnets, Improv, and Selfies”: [http://youtu.be/vqdcejLAuU0?t=7m55s](http://youtu.be/vqdcejLAuU0?t=7m55s).


Here is a transcript of the commentary about augmented reality that begins at 7:55: “To give you a first-person view, I’ll attach Glass through a camera.
When the user taps Glass, a picture is taken, and AR tags are detected.
The detected tag IDs are rendered in an overlay the size of the original picture.
The overlay can be modified directly in JavaScript, opening up a wide range of augmented reality applications on Glass.
Subsequent pictures are aligned to the original using image registration.
We can then warp the overlay to a picture from the user’s current viewpoint, and then, using our prism-to-camera calibration, which we’ve described in previous videos, warp the overlay to align with the user’s view”.
 
**15       **Advantages of eye tracking:****

 
**15.1**Already using your eyes****

 
Most people are already using their eyes in computer interaction anyway.
 
For example, before you move your mouse to select something, it is very likely that you’ve already seen the target.
The same thing goes for touch user interfaces.
Most of the time, a person will see a widget that they want to touch before they actually reach out, and physically touch it.
 
**15.2     **Comfort and ergonomics****

 
I know of people that experimented with a touchscreen in a desktop environment.
The problem was that it was too un-ergonomical to keep reaching outwards, as the shoulders tire out fast.

I’ve seen plenty of pictures of environments with 3+ monitors, and I don't think that repeatedly lifting the arms to touch the screens would be comfortable over time.

Gorilla arm syndrome: "failure to understand the ergonomics of vertically mounted touchscreens for prolonged use.
By this proposition the human arm held in an unsupported horizontal position rapidly becomes fatigued and painful".
 
[http://en.wikipedia.org/wiki/Touchscreen#.22Gorilla_arm.22](http://en.wikipedia.org/wiki/Touchscreen#.22Gorilla_arm.22)
 
**15.2.1**Vertical touchscreen pain****

 
Windows 8 touchscreen pain
 
“In fact, according to many experts, using a touchscreen in a vertical position is very risky ergonomically.
With touchscreen notebooks comparatively new, most research relates to desktops.
But while the problems with notebooks may not be as extreme, they still apply.
 
Indeed, Apple's Steve Jobs – not usually one to dismiss a pretty gadget on the grounds of uselessness – once said he'd never launch a touchscreen laptop because of what he called "gorilla arm".
 
"We've done tons of user testing on this," he said back in 2010, "and it turns out it doesn't work.
Touch surfaces don't want to be vertical.
It gives great demo, but after a short period of time you start to fatigue, and after an extended period of time, your arm wants to fall off."
 
It is possible, of course, to position a laptop so that the screen is reachable without lifting the elbows from the desk; but this means bringing it much closer than most people find comfortable visually.
 
Microsoft's online advice on using a PC safely doesn't mention touchscreens at all – and, ironically, instructs users to avoid just those movements that a touchscreen notebook demands.
 
A company spokesperson said Microsoft had no advice for users about safe use of the Surface touchscreen, and no comment about possible health issues.”
 
[http://www.theguardian.com/technology/2013/apr/09/windows-8-touchscreen-laptops-pain](http://www.theguardian.com/technology/2013/apr/09/windows-8-touchscreen-laptops-pain)
 
“Although we reached out to Microsoft for this story, the company did not respond to our request to comment.
 
In order to touch the display on a notebook with that capability, users either have to fully extend their arm (bad and uncomfortable), lean forward (bad and awkward) or move the display closer (bad for your vision).”
 
[http://blog.laptopmag.com/are-windows-8-touch-laptops-bad-for-your-health](http://blog.laptopmag.com/are-windows-8-touch-laptops-bad-for-your-health)

Eye control can help you avoid these problems.
 
**15.3     **Augmentation, not replacement – “click-where-I’m-looking-at” keyboard button, or cursor teleport before using mouse****

 
Eye control can be an additional input that works together with your hands.

e.g. you can use a macro program like Autohotkey or AutoIt to remap a keyboard button to click.

Appskey::Click

Look at any interface element to highlight it, and then touch the application key on the keyboard to left-click, and select it.
 
If you instead need the precision of the mouse, you can use eye tracking to first teleport the pointer to your target, and then let the mouse override at the end.
 
**15.4     **Bringing speed, recognition, and malleability of virtual buttons in a touch UI to desktop users and vertical touchscreen users that are using a non-touch UI****

When using Autohotkey for remapping buttons, I sometimes didn't have enough unused keyboard buttons to attach macros and lines of code to them, so I'd have to make new scripts that use the same button.
After more buttons and scripts, it can be easy to forget which button does what.

With your eyes being able to cover large distances on a screen quickly, fast activation of on-screen interface elements without a touchscreen is now more feasible.
It virtually turns a non-touch screen into a touchscreen.


You can instantly invoke custom, virtual, on-screen buttons that have your macros and commands that are attached to them.
With on-screen buttons and controls, you can design them to look however you want.
Button labels can be descriptive and self-documenting.
Attaching macros to a growing list of keyboard shortcuts that use Control + Alt + Shift + <whatever> can be more difficult to memorize and maintain.
It would be much easier to build, support, and recognize a collection of customizable and virtual buttons, than rely only on limited and static physical keys.


**15.4.1    **e.g. Control + <whatever> = action vs. visual shortcut: button that is labeled with action****

e.g. I remapped Control + F1 to launch a google search on whatever is on the clipboard:
^F1::Run google/com/search?hl=en&safe=off&q=%Clipboard% .
 
With another script, Control +F1could execute something completely different.
Within a single script, depending on the context, such as what program is currently running, or what window or dialog is in focus, the use of Control +F1could change again; it can get confusing.

It would be more intuitive to look at a virtual button that is actually labeled, "Google Search the Clipboard", and then tap my activation key.
 
**15.4.2**Sharing easily learnable scripts and visual interfaces e.g. sharing Gazespeaker grids as XML files****

 
As users of speech command programs, you already know this advantage, as you can create almost any series of natural language terms to activate your speech commands.
It’s probably easier to learn a new set of speech commands than a set of Control + Alt + Shift + <whatever> keyboard shortcuts because what you say can be the same as the action.
 
Although, visual interfaces, like on-screen buttons, would require even less learning and memorization as the labels are constantly in view.
Therefore, it will be very easy for people to understand the sample scripts and interfaces that will be shared with one another.
If they’re edited, tweaked, and re-shared, people will be able to see the changes more immediately, and learn them much faster
 
An example was mentioned above in the heading, “Sharing custom grids and cells”, where Gazespeaker grids that are stored in XML files can be shared with other people.


Interfaces that involve activating visual elements are more likely to become widespread than interfaces that require one to recall large lists of keyboard shortcuts.
 
**15.5**Using only a keyboard for maximum speed****

 
**15.5.1**Elements that are hard to access, or access quickly by keyboard****

 
You can try to rely on just a keyboard, and have all the shortcut mnemonics memorized, but not every element has an underlined letter e.g. items in a list box, or bookmarks in a bookmark toolbar.
Also, if you are using something like Vimium to generate keyboard shortcuts for web links, you can’t memorize them because they’re randomly generated every time.
A “touch/click-where-I’m-looking” keyboard button can help you quickly access the rest.


**15.5.2**E.g. editing code without using a mouse: “fold-the-block-of-code-that-I’m-looking-at”****

 
“Ctrl+NumPad- (Minus) = Fold method, class or any other foldable block of code at caret”.
 
Just look at the block of code, and press Ctrl+NumPad-.
 
Not only can an eye-controlled cursor be more instant then a mouse-controlled cursor, but replacing the mouse in certain instances means that you don’t have to keep lifting a hand away from the keyboard to use a mouse.
 
**15.6**Mobile touch: eye-highlighting + only needing a few buttons (e.g. “single-tap-where-I’m-looking”, “double-tap-where-I’m-looking”) – hands-free scrolling – vertical mobile touchscreen – two-step process for selecting smaller elements, like text links, on non-touch-optimized websites while using mobile****

 
**15.6.1**Touch gestures + “touch-where-I’m-looking” buttons vs. touch gestures alone vs. mouse-clicking on a desktop****


Eye-highlighting + few "tap-where-I’m-looking” function buttons
 
If you had eye control on a touch device, you could have a few go-to, base, function buttons (could be two or three) that you can press after you highlight something with your eyes.
One of the buttons could be a “tap-where-I’m-looking” button.
 
Look, touch an easy-to-reach “tap-where-I’m-looking” button, look, and then touch the same button again.
You don’t have to keep changing your hand and finger positions between each tap.
 
Touch alone: multiple touch gestures for different actions

Currently, if I take something like the Chrome app icon on the home screen of Android, I can tap it to open it, or long-press/hold it to move it.
(There's also double tap, triple tap, and swiping that are available for use).

Desktop: different types of mouse clicking for different actions

For the desktop, left and right single-click, left and right double-click, left and right mouse-drag, and the middle mouse click are some examples of mouse clicking that achieve different actions on a target once a mouse cursor is on it.
 
**15.6.1.1**Advantages of eye tracking + few function buttons: speed, comfort, and less finger and hand movement – single-taps and tablets****


Single-tapping keys would probably be faster and more comfortable than repeatedly doing double-clicks, double-taps, long-presses/holds, swipes, or multi-finger gestures, such as pinching and zooming.
 
On top of only needing single taps, since you may only require a few buttons, your thumbs or fingers reach out for much fewer things.
If you’re working with a larger, tablet-sized screen which requires more hand movement to reach all the buttons and widgets, then assigning yourself to merely a few buttons and hand positions would give you even more of a speed and comfort advantage over those that don’t incorporate eye input.
 
**15.6.1.2**Example apps on mobile****

 
**15.6.1.2.1**Customizing the Android Navigation Bar (easy-to-reach buttons)****

 
E.g. There are applications like Ultimate Dynamic Navbar which allow you to customize the easily reachable Android Navigation Bar.
Besides the three default buttons, you could add “single-tap-where-I’m-looking”, and “swipe-up-where-I’m-looking” (to perhaps simulate a Page Down for reading) buttons, and a couple other buttons (although just a “single-tap-where-I’m-looking” button should allow you to do a lot of things).
 
**15.6.1.2.2**Eye Tribe’s Android demo: tap anywhere on the screen****

 
“Looking at icons on a desktop instantly highlights them, and you can then tap anywhere on the screen to open up the selected app.” ([http://www.stuff.tv/mwc-2014/eyes-eye-tribe-we-play-fruit-ninja-using-nothing-our-eyeballs/feature](http://www.stuff.tv/mwc-2014/eyes-eye-tribe-we-play-fruit-ninja-using-nothing-our-eyeballs/feature)).
 
I guess that in one of Eye Tribe’s demos, they temporarily made the entire screen a “tap-where-I’m-looking” button.
 
**15.6.1.2.3**Launchers that require more than just taps i.e. swiping, double taps – replace with eye tracking + single-taps****

 
E.g. In addition to the normal opening of a Home screen Android icon with a single tap, the Action Launcher 2.0 app allows you to swipe-up/down or double-tap on an icon after an icon modification to open a branch of related icons (i.e. an Android folder), such as other shortcuts, or small Android widgets.
You can also swipe-up/down or double tap on an icon after a different kind of icon modification to open a full screen Android widget of the program that corresponds to that icon.


Since this application can demand more swiping and double-tapping, quick, more-easier-to-reach taps of a “swipe-where-I’m-looking”, or “double-tap-where-I’m-looking” button can help here.
**15.6.1.2.4**Eye Tribe’s corner thumb buttons****

 
In a presentation at NEXT Berlin, Eye Tribe demonstrates a tablet interface ([http://youtu.be/rAlclfa-9uY?t=8m12s](http://youtu.be/rAlclfa-9uY?t=8m12s)) where there are two corner buttons for each thumb.
 
This shows that combining eye tracking makes an interface require as little as two buttons to do many things.
 
**15.6.2**Vertical touchscreen + “tap-where-I’m-looking” button****

 
If you have a vertically propped up tablet with an external keyboard, you could remap a keyboard button to be the “tap-where-I’m-looking” button, and avoid the need to keep reaching out to touch the screen.
 
**15.6.3**Hands-free interaction: while eating, while using another computer, etc.****

 
Eye-tracking gives you the ability to have a page automatically scroll down when your eyes reach the bottom of the window ([http://youtu.be/2q9DarPET0o?t=22s](http://youtu.be/2q9DarPET0o?t=22s)), or have an e-book automatically turn the page when the gaze reaches the corner of the text ([http://youtu.be/2q9DarPET0o?t=1m19s](http://youtu.be/2q9DarPET0o?t=1m19s)).
These features would be especially handy for computer interaction while cooking and eating.
They could also be for interacting with a vertically set up touch device, or laptop that is more than an arms-length away while doing other stuff on a desktop computer.
 
**15.6.4**Two-step process for selecting harder-to-press links and characters on non-touch-optimized (or touch-optimized) websites while using mobile****

 
As mentioned above, touch interfaces have a two-step magnification feature for selecting elements that are smaller and/or too close together.
Here’s a picture of magnification in Chrome on Android: ([http://i.stack.imgur.com/95nHA.png](http://i.stack.imgur.com/95nHA.png)).
It occasionally appears when interacting on non-mobile, desktop versions of a website that are crowded with smaller elements.
 
However, even mobile-friendly and touch-optimized websites can still have small elements.
 
For example, if you look at Reddit’s mobile site, some buttons may be larger, but text links can still be quite skinny and narrow.
When links are tightly and vertically stacked, a user may have to be more meticulous and tense with their motions.
 
If you pinch-zoom-out to get a larger view of a website, small elements and links that are close together will get even smaller.
 
Since a two-step magnification process already exists for touch, the projected elements could be made to be just a bit larger for eye-tracking.

Look at a target element, and then quickly activate a “simulate-a-cautious-placement-of-the-finger-and-long-press” button that could be in the Navigation Bar.
It zooms in on the target element, and projects some of the smaller elements into large elements.
A user could then quickly re-touch the “cautious-placement-and-long-press” button to select it, or briefly dwell on the choice large element to select it.
 
**15.6.4.1**Eye-tracking two-step process for selecting a range of characters and words****

 
Just like selecting text links, a task like selecting a range of characters and words can be more arduous than selecting possibly wider website buttons.
 
For text selection, there could be a process that is similar to the drag-and-drop of the PCEye software that was mentioned above, where a zoom-in is used twice: a magnification is used on what’s picked up, and a magnification is used on where the picked-up item will go.
 
Look at the first character, and then explicitly activate a text-selection widget that could be in the Navigation Bar.
It zooms in to where you're looking at, and then projects some of the smaller characters that are near the point-of-gaze into large elements.
Look at the larger element that corresponds to the first character, and then you could quickly re-tap the text-selection widget to select the character, or dwell on the larger element to select the character.
It zooms out to let you find the last character, and then you repeat the magnification and selection on the last character to complete the range selection.

This could be a better way of selecting text on a smart phone or tablet.
It could be an alternative to putting possibly thick thumbs on a tiny target character or word, long pressing/holding to begin the range, and then possibly dragging the two selection indicators over long distances (possibly larger than the current viewport) on a small screen with small font.
At the very least, it can be more comfortable.
 
**15.7     **Future: head-mounted display with eye tracking + armband, watch, ring, computer vision system, augmented reality system, etc. for input (helps work with limited space and limited gestures)****

 
Select your target element with eye tracking on Glass, and then tap one of the few function buttons that could be on another device, or then use a few touchless gestures.
 
**15.7.1**Watches – small screen real estate works with eye-tracking****

 
From pictures of smart watches like Galaxy Gear and WiMM, it looks like it has a display with room for 4 large-sized widgets, and I have read that the Pebble watch has 4 buttons.
The Samsung Gear Live, LG G, and Moto 360 watches also have smaller screen sizes.
These smaller screen sizes are acceptable because as mentioned above, incorporating eye tracking means that you can get away with only needing to touch a few function buttons.
 
**15.7.2**Clothes: Makey Makey and OpenShades****

 
In Brandyn White’s OpenShades Google Glass eye tracking video, he wires a Makey Makey (turns everyday objects into touchpads) to his shirt, and taps his clothes whenever he wants to do an action.
“New Glass Input Methods: Eye-Tracking, Web Control, Touch-Sensitive Clothing, and Bananas”: [https://www.youtube.com/watch?v=QSn6s3DPTSg](https://www.youtube.com/watch?v=QSn6s3DPTSg).
Tapping the left shoulder is one action, and tapping the right shoulder is another.
That’s only two spots.
 
**15.7.3**Computer vision recognition of forearm (Minuum video) – overlay augmented reality keys on forearm****

 
The Minuum video demonstrates computer vision on Glass recognizing a user’s forearm, and an augmented reality system overlaying the forearm with keys.
 
Compared to a physical keyboard, a forearm doesn’t have a lot of space.
 
**15.7.4**Gestures****

 
**15.7.4.1**While mobile: armbands, rings****

 
The amount of gestures that you can make with the Myo armband, Fin (thumb ring), Mycestro (index ring), Nod (ring), and Ring (another ring) might be limited by the number of physically-easy motions that you can do, and having to memorize all of them.
 
**15.7.4.2**While stationary: Tango, Haptix/Touch+, Leap Motion Table mode****

 
**15.7.4.2.1**Haptix/Touch+(transform any flat surface into a 3-D multitouch surface)****

 
There is a device called Touch+ (formerly known as the Haptix KickStarter) ([https://www.kickstarter.com/projects/haptix/haptix-multitouch-reinvented](https://www.kickstarter.com/projects/haptix/haptix-multitouch-reinvented)) that transforms any flat surface into a 3-D multitouch surface.
It’s kind of like the Leap Motion, but it doesn’t focus on air gestures.
Touch+ faces downwards to a surface, and doesn’t require infrared, as  opposed to the Leap Motion that faces upwards, and requires infrared.

Touch+: Make any surface multitouch and more
[https://www.youtube.com/watch?v=6vl2e2EewiM](https://www.youtube.com/watch?v=6vl2e2EewiM)
Touch+ surface gestures vs. Leap Motion air gestures:
[https://www.youtube.com/watch?v=0MUxmqYwcYU](https://www.youtube.com/watch?v=0MUxmqYwcYU)
 
A disadvantage of Touch+ compared to a Laser Keyboard is that it doesn’t project anything on the surface to see where to press (overlaying augmented reality buttons on a surface by using computer vision, as shown in the Minuum video, is not available yet.
Although, a company called Ostendo is looking to bring its 2-D and 3-D miniature projectors, and holograms to smart phones and other consumer devices in 2015).
 
Since you only need a few buttons with eye tracking (e.g. “single-click-where-I’m-looking”, “double-click-where-I’m-looking”, etc.), perhaps you could divide your surface into a few large regions.
It could be 3 x 3, and nine cells for nine actions would still be enough to do a lot.
The areas would be large, so you wouldn’t need a projection to tell you exactly where to press.
 
(If you’re wondering about losing the physical keyboard letters in this set up, Touch+ partnered with the ASETNIOP virtual keyboard.
ASETNIOP is "QWERTY with only 10 keys...
this virtual keyboard enlarges eight common letters -- a, s, e, t, n, i, o, p.
The rest of the alphabet is input by simple "chord" combos of fingers.
Good typists can clock 80 wpm.".
 
Like Fleksy, ASETNIOP allows you to type without looking.
ASETNIOP + Haptix  = fast typing on any surface: [https://www.youtube.com/watch?v=hyQo8uCVOXs](https://www.youtube.com/watch?v=hyQo8uCVOXs).
 
Here is a video of a user typing at over 100 wpm on an iPad with ASETNIOP: [https://www.youtube.com/watch?v=fP2TH7TQC8w](https://www.youtube.com/watch?v=fP2TH7TQC8w)).
 
**15.7.4.2.2**Leap Motion Table mode (interact with surfaces) – if using air gestures without eye tracking, many more-physically-demanding gestures to memorize****

 
A much coveted feature for Leap Motion is “Table mode”, which would allow users of Leap Motion to interact with surfaces, just like Touch+ can.
 
A user was able to get Table mode with Leap Motion by hacking together some transparent glass so that the Leap Motion could see through the surface, and distinguish the hands.
Here’s a video of the user playing Reflex.te, a reaction game that’s usually meant for the mouse: [https://www.youtube.com/watch?v=cgGkwGJcB1c](https://www.youtube.com/watch?v=cgGkwGJcB1c).


GameWAVE is an app in Leap Motion’s app store.
“Uwyn’s GameWAVE, available for Mac and Windows, recently debuted in Airspace.
It allows you to completely control keyboard and mouse-based video games, as well as your OS”.
“20 distinct swipe and circle gestures, 6 continuous movement”.
 
Instead of 20 unique gestures for 20 actions, you could just have one Leap Motion gesture to bring up a menu of 20 on-screen buttons, and then use a “select-what-am-looking-at” gesture to activate one of the virtual buttons.
 
**15.7.4.2.3**Project Tango and Movidius chip****

 
Google’s Project Tango device (like a portable Kinect) has the Movidius chip: “New applications include post-capture refocusing, high quality zoom, augmented reality simulation, gaze or gesture-based user interfaces”.
 
If you were to sit, and plant down Project Tango, it might similarly record your gestures.
(It’s supposedly coming to consumers in 2015).
 
**15.7.5**Conclusion****

 
With the limited number of easily-memorizable gestures, or limited space for taps and gestures, these devices would benefit with eye tracking, which could be found in a head-mounted device.
Eye-tracking would reduce the number of inputs needed.
                                     
At the same time, the head-mounted device with eye-tracking could use the devices mentioned above for inputting.
It would provide a better way to do lengthy and rapid interactions with devices like Google Glass.
You wouldn’t have to constantly reach at your head, and lift your arms for long periods of time.
 
**15.7.6**Oculus Rift + eye tracking****

 
**15.7.6.1**Oculus Rift with the Haytham gaze tracker****

 
Researchers from ITU (where I think Eye Tribe comes from) added eye-tracking to the Oculus Rift with the Haytham gaze tracker, and OpenCV.
(Haytham is an open source gaze tracker from the IT University of Copenhagenlike, just like the ITU Gaze Tracker).
 
[http://www.itu.dk/research/eye/?page_id=671](http://www.itu.dk/research/eye/?page_id=671)
 
**15.7.6.2**Selecting and manipulating virtual objects with more speed and comfort, and less hand positions – e.g. Oculus Rift with camera for augmented reality****

 
AR-Rift: Stereo camera rig and augmented reality showcase: Virtual screens:
[http://youtu.be/Bc_TCLoH2CA?t=12m25s](http://youtu.be/Bc_TCLoH2CA?t=12m25s).
 
In this video, a person attaches cameras to the Oculus Rift to see the real world, and augments reality with virtual objects.
At 12:25, the person moves virtual screens around by repeatedly lifting his arms, and activates menu items by making virtual objects touch each other.


With eye-tracking, selecting items in a floating virtual menu, and other objects in the world could be quick, just like with regular 2-D on-screen buttons.


If air gestures are used, like in the video, then eye tracking could also help replace some of the gestures, and thus mitigate horizontal-arm ergonomic problems.
 
He’s also able to switch from augmented reality to full virtual reality.
In this mode, there is no easy way to see your physical arms interacting with a physical keyboard.
Eye-tracking can minimize the amount of buttons and hand positions that are needed, so not being able to see and use all the buttons of a physical keyboard are less of a problem.
 
**15.7.6.3**Navigating 20 virtual stock trading screens in Oculus Rift****

 
Traders can have 12 or more monitors for prices, news, charts, analytics, financial data, alerts, messages, etc..
Bloomberg LP (makes financial software) built a virtual prototype of their data terminal for the Oculus Rift.
Here is the image of their prototype with 20 virtual screens: [http://i.imgur.com/Z9atPdh.png](http://i.imgur.com/Z9atPdh.png)
 
You may have no problem with moving a mouse-controlled cursor across 1 screen, but what happens if you want to one day have 4+ virtual screens? Moving a cursor with a mouse across 4+ screens would probably be more difficult, so eye-tracking teleportation would really help here.
 
**15.7.6.4**Oculus Rift + eye tracking for traversal - non-gamers – “go-to-where-I’m-looking-at” e.g. eye-tracking wheelchair by researchers at Imperial College London****

 
Also, integrating an eye tracker into the Oculus Rift could really help with traversing around.
Look at where you want to go, and then press a “go-to-where-I’m-looking-at” button to auto-move to that location.
 
Eye-tracking wheelchair – "move around simply by looking to where they wish to travel" - also for robots and drones
 
“Scientists in London have developed an algorithm-based decoder system that enables wheelchair users to move around simply by looking to where they wish to travel.
The researchers at Imperial College London say the system is inexpensive and easy to use and could transform the lives of people who are unable to use their limbs”.
“You could use it maybe one day to drive your car, you could use it to operate a robot, you may be able to use it to fly planes or drones or spaceships with this type of technology." [https://www.youtube.com/watch?v=ZckE7FMWrw8](https://www.youtube.com/watch?v=ZckE7FMWrw8).


The roller coaster demo on the Oculus Rift shows that people of all ages can enjoy the device.
And there was that video of the 90-year-old grandmother ([https://www.youtube.com/watch?v=pAC5SeNH8jw](https://www.youtube.com/watch?v=pAC5SeNH8jw)) being absolutely in love with the Tuscany demo.
A family member was controlling her character in the virtual world.
If she wanted to move by herself, the Virtuix Omni or Cyberith Virtualizer treadmills, or a game controller would probably be too difficult to use.
 
**16       **Conclusion****

 
Eye-tracking can clearly help with accessibility, but almost everyone would see their productivity increase by integrating eye tracking.


**17       **Communities****

 
[http://www.tendinosis.org/forum](http://www.tendinosis.org/forum)
 
[http://www.reddit.com/r/EyeTracking](http://www.reddit.com/r/EyeTracking)
 
Disability & Assistive Technology Today: [https://plus.google.com/u/0/communities/100493067912302632679](https://plus.google.com/u/0/communities/100493067912302632679)
 
[http://www.reddit.com/r/RSI](http://www.reddit.com/r/RSI)
 
[https://www.facebook.com/RSISupportGroup](https://www.facebook.com/RSISupportGroup)
 
[http://www.sorehand.org/](http://www.sorehand.org/)
 
Tendinosis Google+ Community: [https://plus.google.com/u/0/communities/115101160005972411030](https://plus.google.com/u/0/communities/115101160005972411030)
 
TalkingEyes: Eye-tracking and ALS Google+ Community: [https://plus.google.com/u/0/communities/103103072435695270907](https://plus.google.com/u/0/communities/103103072435695270907)
 
[http://theeyetribe.com/forum/](http://theeyetribe.com/forum/)
(There is a computer control section, and an accessibility section)
 
[http://developer.tobii.com/community-forums/](http://developer.tobii.com/community-forums/)
 
Voice Coder: [http://groups.yahoo.com/neo/groups/VoiceCoder/info](http://groups.yahoo.com/neo/groups/VoiceCoder/info)
 
Palaver speech recognition: [https://plus.google.com/communities/117295420902112738135](https://plus.google.com/communities/117295420902112738135)
 
Eye Tracking: [https://plus.google.com/u/0/communities/111368046513443831724](https://plus.google.com/u/0/communities/111368046513443831724)
 
Speech recognition community: [https://plus.google.com/u/0/communities/102115132514072731857](https://plus.google.com/u/0/communities/102115132514072731857)
 
Computer Accessibility: [https://plus.google.com/u/0/communities/110852840897935418793](https://plus.google.com/u/0/communities/110852840897935418793)
 
Web Accessibility: [https://plus.google.com/u/0/communities/107472407495224690148](https://plus.google.com/u/0/communities/107472407495224690148)
 
LiSpeak - Linux Voice Command System: [https://plus.google.com/communities/115594832299044979120](https://plus.google.com/communities/115594832299044979120)
 
Quadriplegia: [https://plus.google.com/u/0/communities/110899974755252591010](https://plus.google.com/u/0/communities/110899974755252591010)
 
#ux #design #ui #usability [#tendinitis]("https://plus.google.com/s/%23tendinitis") [#tendonitis]("https://plus.google.com/s/%23tendonitis") [#repetitivestraininjury]("https://plus.google.com/s/%23repetitivestraininjury") #rsi [#repetitivestrain]("https://plus.google.com/s/%23repetitivestrain") [#a11y]("http://www.youtube.com/results?search_query=a11y") #Google [#palaver]("https://plus.google.com/s/%23palaver") [#AAC]("https://plus.google.com/s/%23AAC") [#stroke]("https://plus.google.com/s/%23stroke") [#strokerecovery]("https://plus.google.com/s/%23strokerecovery") [#spinalcordinjury]("https://plus.google.com/s/%23spinalcordinjury") #quadriplegia [#googleglass]("https://plus.google.com/s/%23googleglass") [#cerebralpalsy]("https://plus.google.com/s/%23cerebralpalsy") [#hci]("https://plus.google.com/s/%23hci") [#humancomputerinteraction]("https://plus.google.com/s/%23humancomputerinteraction")  &#65279;

---

