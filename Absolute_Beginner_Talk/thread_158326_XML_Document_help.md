---
title: "XML Document help"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by slipk487 on 2006-04-10
this my be off subject but does anybody know why i would get this error when opening my xml document

```
XML Parsing Error: not well-formed
Location: http://www.filelodge.com/files/hdd5/111048/SamplePlaylist.xml
Line Number 47, Column 72:  <song path="http://www.filelodge.com/files/hdd5/111048/13%20Blood%20&%20Flames.mp3" title="Blood & Flames - Jesse David Leach; Matthew K. Heafy" />
-----------------------------------------------------------------------^
```
[the file is here]("http://www.filelodge.com/files/hdd5/111048/SamplePlaylist.xml")
and here is my coding

```
<?xml version="1.0" encoding="UTF-8"?> 

  

<songs>

  <song path="http://www.filelodge.com/files/hdd5/111048/01%20-%20Black%20Label.mp3" title="Black Label - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/02%20-%20A%20Warning.mp3" title="A Warning - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/03%20-%20In%20the%20Absence%20of%20the%20Sacred.mp3" title="Absence of the Sacred - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/04%20Letter%20to%20the%20Unborn.mp3" title="Letter to the Unborn - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/05%20-%20The%20Black%20Dahlia.mp3" title="The Black Dahlia - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/06%20-%20Terror%20and%20Hubris.mp3" title="Terror and Hubris - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/07%20-%20The%20Subtle%20Arts%20of%20Murder%20and%20Persuasion.mp3" title="The Subtle Arts of Murder and Persuasion - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/08%20-%20Pariah.mp3" title="Pariah - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/09%20-%20Confessional.mp3" title="Confessional - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/10%20-%20O.D.H.G.A.B.F.E.mp3" title="O.D.H.G.A.B.F.E - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/11%20-%20Nippon.mp3" title="Nippon - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/01%20Ruin.mp3" title="Ruin - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/02%20As%20the%20Palaces%20Burn.mp3" title="As the Palaces Burn - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/03%20Purified.mp3" title="Puirfied - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/11thHour.mp3" title="11th Hour - Lamb of God" /> 

  <song path="http://www.filelodge.com/files/hdd5/111048/05%20For%20Your%20Malice.mp3" title="For Your Malice - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/06%20Boot%20Scraper.mp3" title="Boot Scraper - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/07%20A%20Devil%20in%20Gods%20Country.mp3" title="A Devil in God's Country - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/08%20In%20Defense%20of%20Our%20Good%20Name.mp3" title="In Defense of Our Good Name - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/09%20Blood%20Junkie.mp3" title="Blood Junkie - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/10%20Vigil.mp3" title="Vigil - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/01%20Laid%20to%20Rest.mp3" title="Laid To Rest - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/02%20Hourglass.mp3" title="Hourglass - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/03%20Now%20Youve%20Got%20Something%20to%20Die%20For.mp3" title="Now You've Got Something to Die For - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/04%20The%20Faded%20Line.mp3" title="The Faded Line - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/05%20Omerta.mp3" title="Omerta - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/06%20Blood%20of%20the%20Scribe.mp3" title="Blood of the Scribe - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/07%20One%20Gun.mp3" title="One Gun - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/08%20Break%20You.mp3" title="Break You - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/09%20What%20Ive%20Become.mp3" title="What I've Become - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/10%20Ashes%20of%20the%20Wake%20%5BInstrumental%5D.mp3" title="Ashes of the Wake - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/11%20Remorse%20Is%20for%20the%20Dead.mp3" title="Remorse is for the Dead - Lamb of God" />

  <song path="http://www.filelodge.com/files/hdd5/111048/01%20The%20Dagger.mp3" title="The Dagger - Howard Jones; Robert Flynn" />

  <song path="http://www.filelodge.com/files/hdd5/111048/02%20The%20Enemy.mp3" title="The Enemy - Dino Cazares; Mark Hunter; Roy Mayorga" />

  <song path="http://www.filelodge.com/files/hdd5/111048/03%20Annihilation%20by%20the%20Hands%20of%20God.mp3" title="Annihilation by the Hands of God - Glen Benton; Joey Jordison; Rob Barrett" />

  <song path="http://www.filelodge.com/files/hdd5/111048/04%20In%20the%20Fire.mp3" title="In the Fire - King Diamond; Matthew K. Heafy" />

  <song path="http://www.filelodge.com/files/hdd5/111048/05%20The%20End.mp3" title="The End - Dino Cazares; Matthew K. Heafy" />

  <song path="http://www.filelodge.com/files/hdd5/111048/06%20Tired%20N%20Lonely.mp3" title="Joey Jordison; Keith Caputo - Tired 'N Lonely" />

  <song path="http://www.filelodge.com/files/hdd5/111048/07%20Independent%20(Voice%20of%20the%20Voiceless).mp3" title="Independent (Voice of the Voiceless) - Max Cavalera; Phil Demmel; Robert Flynn" />

  <song path="http://www.filelodge.com/files/hdd5/111048/08%20Dawn%20of%20a%20Golden%20Age.mp3" title="Dawn of a Golden Age - Dani Filth; Matthew K. Heafy" />

  <song path="http://www.filelodge.com/files/hdd5/111048/09%20The%20Rich%20Man.mp3" title="The Rich Man - Corey Taylor; Robert Flynn" />

  <song path="http://www.filelodge.com/files/hdd5/111048/10%20No%20Way%20Out.mp3" title="No Way Out - Daryl Palumbo; Joey Jordison; Matt Sepanic" />

  <song path="http://www.filelodge.com/files/hdd5/111048/11%20Baptized%20in%20the%20Redemption.mp3" title="Baptized in the Redemption - Dez Fafara; Dino Cazares; Roy Mayorga" />

  <song path="http://www.filelodge.com/files/hdd5/111048/13%20Blood%20&%20Flames.mp3" title="Blood & Flames - Jesse David Leach; Matthew K. Heafy" />

  <song path="http://www.filelodge.com/files/hdd5/111048/14%20Constitution%20Down.mp3" title="Constitution Down - Joey Jordison; Kyle Thomas" />

  <song path="http://www.filelodge.com/files/hdd5/111048/15%20I%20Dont%20Wanna%20Be%20(A%20Superhero)..mp3" title="I Don't Wanna Be (A Superhero) - Matthew K. Heafy; Michale Graves" />

  <song path="http://www.filelodge.com/files/hdd5/111048/16%20Army%20of%20the%20Sun.mp3" title="Army of the Sun - Dave McClain; Robert Flynn; Tim Williams" />

  <song path="http://www.filelodge.com/files/hdd5/111048/17%20No%20Mas%20Control.mp3" title="No Mas Control - Cristian Machado; Dino Cazares; John Sankey" />

  <song path="http://www.filelodge.com/files/hdd5/111048/18%20Enemy%20of%20the%20State.mp3" title="Enemy of the State - Joey Jordison; Matt Sepanic; Pete Steele" />

  <song path="http://www.filelodge.com/files/hdd5/111048/01%20-%20The Dark Ages.mp3" title="The Dark Ages - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/02%20-%20Babylon.mp3" title="Babylon - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/03%20-%20I and I.mp3" title="I and I - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/04%20-%20Carved%20Inside.mp3" title="Carved Inside - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/05%20-%20Arise%20Again.mp3" title="Arise Again - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/06%20-%20Molotov.mp3" title="Molotov - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/07%20-%20Frontlines.mp3" title="Frontlines - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/08%20-%20Innerspirit.mp3" title="Innerspirit - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/09%20-%20Corrosion Creeps.mp3" title="Corrosion Creeps - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/10%20-%20Riotstarter.mp3" title="Riotstarter - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/11%20-%20Bleak.mp3" title="Bleak - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/12%20-%20The%20March.mp3" title="The March - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/13%20-%20Fuel%20the%20Hate.mp3" title="Fuel the Hate - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/14%20-%20Staystrong.mp3" title="Staystrong - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/15%20-%20Soulfly%20V.mp3" title="Soulfly V - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/02%20-%20Torn%20Within.mp3" title="Torn Within - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/03%20Forced%20to%20Die.mp3" title="Forced to Die - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/04%20A%20Breath%20in%20the%20Eyes%20of%20Eternity.mp3" title="A Breath in the Eyes of Eternity - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/05%20Blood%20Turned%20to%20Tears.mp3" title="Blood Turned to Tears - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/06%20The%20Voices%20That%20Betray%20Me.mp3" title="The Voices That Betray Me - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/07%20When%20This%20World%20Fades.mp3" title="When This World Fades - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/09%20Surrounded.mp3" title="Surrounded - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/11%20The%20Innocence%20Spilled.mp3" title="The Innocence Spilled - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/01%2094%20Hours.mp3" title="94 Hours - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/02%20Falling%20Upon%20Deaf%20Ears.mp3" title="Fall Upon Deaf Ears - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/03%20Forever.mp3" title="Forever - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/04%20Collision.mp3" title="Collision - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/05%20Distance%20Is%20Darkness.mp3" title="Distance is Darkness - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/08%20A%20Thousand%20Steps.mp3" title="A Thousand Steps - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/09%20The%20Beginning.mp3" title="The Beginning - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/11%20%20The%20Pain%20of%20Seperation.mp3" title="The Pain of Seperation - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/12%20Elegy.mp3" title="Elegy - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/01%20Meaning%20in%20Tragedy.mp3" title="Meaning in Tragety - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/02%20Confined.mp3" title="Confined - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/03%20Losing%20Sight.mp3" title="Losing Sight - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/04%20-%20The%20Darkest%20Nights.mp3" title="THe Darkest Night - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/05%20Empty%20Hearts.mp3" title="Empty Hearts - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/06%20Reflection.mp3" title="Reflection - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/07%20Repeating%20Yesterday.mp3" title="Repeating Yesterday - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/08%20Through%20Struggle.mp3" title="Throght Struggle - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/09%20The%20Truth%20of%20My%20Perception.mp3" title="The Truth of My Perception - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/10%20Control%20Is%20Dead.mp3" title="Control is Dead - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/11%20-%20Morning%20Waits.mp3" title="Morning Waits - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/12%20Illusions.mp3" title="Illusions - As I Lay Dying" />

  <song path="http://www.filelodge.com/files/hdd5/111048/01%20The%20End%20of%20Everything.mp3" title="The End of Everything - Trivium" />  

  <song path="http://www.filelodge.com/files/hdd5/111048/02%20Rain.mp3" title="Rain - Trivium" />

  <song path="http://www.filelodge.com/files/hdd5/111048/PullHarder.mp3" title="Pull Harder on the Strings of Your Martyr - Trivium" />

  <song path="http://www.filelodge.com/files/hdd5/111048/04%20Drowned%20and%20Torn%20Asunder.mp3" title="Drowned and Torn Asunder - Trivium" />

  <song path="http://www.filelodge.com/files/hdd5/111048/05%20-%20Ascendancy.mp3" title="Ascendacy - Trivium" />

  <song path="http://www.filelodge.com/files/hdd5/111048/06%20-%20A%20Gunshot%20to%20the%20Head%20of%20Trepidation.mp3" title="A Gunshot to the Head of Trepidation - Trivium" />

  <song path="http://www.filelodge.com/files/hdd5/111048/07%20Like%20Light%20to%20the%20Flies.mp3" title="Like Light to the Flies - Trivium" />

  <song path="http://www.filelodge.com/files/hdd5/111048/08%20Dying%20in%20Your%20Arms.mp3" title="Dying in your Arms - Trivium" />

  <song path="http://www.filelodge.com/files/hdd5/111048/09%20The%20Deceived.mp3" title="The Deceived - Trivium" />

  <song path="http://www.filelodge.com/files/hdd5/111048/10%20Suffocating%20Sight.mp3" title="Suffocating Sight - Trivium" />

  <song path="http://www.filelodge.com/files/hdd5/111048/11%20Departure.mp3" title="Departure - Trivium" />

  <song path="http://www.filelodge.com/files/hdd5/111048/12%20Declaration.mp3" title="Declaration - Trivium" />   

  <song path="http://www.filelodge.com/files/hdd5/111048/Purity.mp3" title="Purity - Slipknot" />

  <song path="http://www.filelodge.com/files/hdd5/111048/Prophecy.mp3" title="Prophecy - Soulfly" />

  <song path="http://www.filelodge.com/files/hdd5/111048/Sugar.mp3" title="Sugar - System of a Down" />

  <song path="http://www.filelodge.com/files/hdd5/111048/01%20-%20Nothing%20Remains.mp3" title="Nothing Remains - Chimaira" />

  <song path="http://www.filelodge.com/files/hdd5/111048/02%20-%20Save%20Ourselves.mp3" title="Save Ourselves - Chimaira" />

  <song path="http://www.filelodge.com/files/hdd5/111048/03%20-%20Inside%20The%20Horror.mp3" title="Inside Horror - Chimaira" />

  <song path="http://www.filelodge.com/files/hdd5/111048/04%20-%20Salvation.mp3" title="Salvation - Chimaira" />

  <song path="http://www.filelodge.com/files/hdd5/111048/05%20-%20Comatose.mp3" title="Comatose - Chimaira" />

  <song path="http://www.filelodge.com/files/hdd5/111048/06%20-%20Left%20For%20Dead.mp3" title="Left For Dead - Chimaira" />

  <song path="http://www.filelodge.com/files/hdd5/111048/07%20-%20Everything%20You%20Love.mp3" title="Everything You Love - Chimaira" />

  <song path="http://www.filelodge.com/files/hdd5/111048/08%20-%20Bloodlust.mp3" title="Bloodlust - Chimaira" />

  <song path="http://www.filelodge.com/files/hdd5/111048/09%20-%20Pray%20For%20All.mp3" title="Pray For All - Chimaira" />

  <song path="http://www.filelodge.com/files/hdd5/111048/10%20-%20Lazarus.mp3" title="Lazarus - Chimaira" />

  <song path="" title="Song - Band" />

</songs>





```

---

### Post by htinn on 2006-04-11
Didn't you already post this?

[http://ubuntuforums.org/showthread.php?t=156402](http://ubuntuforums.org/showthread.php?t=156402)

---

### Post by Ozitraveller on 2006-04-11
Try taking & out of the filename.


13%20BloodFlames.mp3

---

### Post by slipk487 on 2006-04-11
i need it there but y would it be causing a problem

---

### Post by Ozitraveller on 2006-04-18
Yes it is causing the problem, the line and column numbers match that character. I took it out and the xml file was then valid.

---

### Post by sn123 on 2006-04-18
[QUOTE=Ozitraveller]Yes it is causing the problem, the line and column numbers match that character. I took it out and the xml file was then valid.[/QUOTE]
You need to escape & with &amp; to make it work.


S

---

