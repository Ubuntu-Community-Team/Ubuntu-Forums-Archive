---
title: "California Team Map"
date: 2007-08-13
forum: California Team - US
---

### Post by Yasumoto on 2007-08-13
So we're trying to set up a map with everyone's location in California, as this should make coordinating face-to-face meetings and other events way easier. (And it's just plain cool :D ) Currently, we have a list of members on our [wiki]("https://wiki.ubuntu.com/CaliforniaTeam/Members"), but I want to get a bit of discussion going as to what information we should post on the list and in the map. So far, I think we need a nick in order to identify everyone, and their zip code in order to locate them, but any ideas about implementing this would be awesome.

---

### Post by dreadlord_chris on 2007-08-13
sounds about right - but where do we enter our ZIP code?

---

### Post by lcafiero on 2007-08-13
Hey, folks --

I fought a losing battle behind my firewall at work last night, hence I was unable to make the meeting. I did, however, enter my name on the member wiki and register my irc nickname. Would look forward to meeting face-to-face or online next time.

Santa Cruz -- home of California's best surf -- is in the house.

Larry Cafiero

---

### Post by mthaddon on 2007-08-13
Just follow the "mapdetails" format that others have posted on there.

A first draft version of the map is available here:

[http://locomaps.greenleaftech.net/california_loco_team/](http://locomaps.greenleaftech.net/california_loco_team/)

If anyone updates the WIki with their details and wants to refresh the map, go to:

[http://locomaps.greenleaftech.net/california_loco_team/refresh](http://locomaps.greenleaftech.net/california_loco_team/refresh)

I'll be working with Yasumoto and others to polish it up a bit, decide what the next steps are, etc.

Thanks, Tom

---

### Post by Scunizi on 2007-08-13
I just added my details to wiki.ubuntu.com/Scunizi and updated the map page.. API works great..If we do it all by zip, will we encounter multiple balloons in one specific location?

---

### Post by mthaddon on 2007-08-13
Yeah, we currently would. There are ways of managing this using the Google API so that it doesn't overwhelm - I think it shows multiple only as you zoom in - but I haven't investigated that yet. Can do that if we get to that stage.

Also, you don't have to put zipcode there. Any address that's parseable by google maps will do.

Current format:

(mapdetails:IRCnick||address/zipcode||comments (optional))

---

### Post by Yasumoto on 2007-08-13
Hey Larry, glad you could get your nick registered :) Feel free to stop by #ubuntu-california any time to say hi.

This is really sweet. I'm going to look around and try to find a good basic tutorial on Google Maps, just to see what else we might be able to do.

EDIT: check [this]("http://www.google.com/apis/maps/documentation/index.html#The_Hello_World_of_Google_Maps") out in case you want to mess around with Google Maps too

---

### Post by bmathis on 2007-08-14
I added myself as well as a shameful plug for my network consulting company:)

---

### Post by mthaddon on 2007-08-14
You can also include html in the details section (links, etc.)

---

### Post by mthaddon on 2007-08-14
I've updated the code so it can parse stuff a bit more intelligently - if you include images from the wiki, it will be able to display those now. Basically it just replaces:

src="/

with:

src="WIKI_URL/

Smileys, etc. should now show up.

Cheers, Tom

---

