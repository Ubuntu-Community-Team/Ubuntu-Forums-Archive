---
title: "I can't launch Penguin Racer"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-05-26
Hello,

I installed Penguin Racer from the repos a few weeks ago. Until a week ago, all I had to do was to select the icon in the Games menu and the game started.

Then it stopped working all of a sudden. I tried finding the game launcher... and successfully found it under root/usr/games/ppracer. When I double clicked on it, nothing happened.

I checked the permissions and saw the I didn't have any privileges to change anything whatsoever. I then  opened the terminal as root and launched the command ppracer. It didn't work. When I changed it to /root/usr/games/ppracer, it worked finally.

How can I set it back to working with mouse clicks like I had it in the first place? Thanks.

---

### Post by Bachstelze on 2007-05-26
What happens when you try to run it from a terminal ?

---

### Post by taurus on 2007-05-26
You installed a game in /root/usr/games/ppracer?  Shouldn't you be installing it to /usr/games instead since you don't have permissions to access /root?

---

### Post by Bachstelze on 2007-05-26
I guess he installed to /usr/games but made the usual "root vs. /root" confusion...

---

### Post by the8thstar on 2007-05-26
I installed ppracer from the repos. It never gave me any choice about the install directory. It just installed itself there.

I don't know the difference b/w root and /root.

When I run it from the terminal as 'ppracer' nothing happens. Not even the hard disk light flashes. When I run '/root/usr/games/ppracer' then the game runs fine.

I guess my life would be easier if I was root instead of a user. How do I do that? Don't tell me that I shouldn't do that... no matter what happens, if the computer decides to crash, it WILL crash whether I'm root or not. That's just Murphy's Law.

---

### Post by taurus on 2007-05-26
What's the output of this command from a terminal?

```
locate ppracer
```
Or
```
sudo find / -name ppracer -print
```

---

### Post by the8thstar on 2007-05-26
Okay, here goes...

> /root/.ppracer
/root/.ppracer/tux.sav
/root/.ppracer/options
/usr/games/ppracer
/usr/share/applications/ppracer.desktop
/usr/share/linda/overrides/ppracer
/usr/share/pixmaps/ppracer-128x128.png
/usr/share/pixmaps/ppracer-64x64.png
/usr/share/pixmaps/ppracer-48x48.png
/usr/share/pixmaps/ppracer-32x32.png
/usr/share/pixmaps/ppracer-16x16.png
/usr/share/pixmaps/ppracer.xpm
/usr/share/games/ppracer
/usr/share/games/ppracer/textures
/usr/share/games/ppracer/textures/snow_button.png
/usr/share/games/ppracer/textures/mask_outline.png
/usr/share/games/ppracer/textures/gaugeenergymask.png
/usr/share/games/ppracer/textures/mask_outline2.png
/usr/share/games/ppracer/textures/gaugespeedmask.png
/usr/share/games/ppracer/textures/menu_top_right.png
/usr/share/games/ppracer/textures/conditions_button.png
/usr/share/games/ppracer/textures/checkmark.png
/usr/share/games/ppracer/textures/menu_top_left.png
/usr/share/games/ppracer/textures/mouse_cursor.png
/usr/share/games/ppracer/textures/tuxlife.png
/usr/share/games/ppracer/textures/menu_bottom_right.png
/usr/share/games/ppracer/textures/gaugeoutline.png
/usr/share/games/ppracer/textures/speedmask.png
/usr/share/games/ppracer/textures/splash.png
/usr/share/games/ppracer/textures/wind_button.png
/usr/share/games/ppracer/textures/snowparticles.png
/usr/share/games/ppracer/textures/nopreview.png
/usr/share/games/ppracer/textures/menu_title.png
/usr/share/games/ppracer/textures/energymask.png
/usr/share/games/ppracer/textures/listbox_arrows.png
/usr/share/games/ppracer/textures/herringicon.png
/usr/share/games/ppracer/textures/noicon.png
/usr/share/games/ppracer/textures/menu_bottom_left.png
/usr/share/games/ppracer/textures/mirror_button.png
/usr/share/games/ppracer/terrains.png
/usr/share/games/ppracer/fonts
/usr/share/games/ppracer/fonts/FreeSansBoldOblique.ttf
/usr/share/games/ppracer/tux_walk.tcl
/usr/share/games/ppracer/sounds
/usr/share/games/ppracer/sounds/fish_pickup1.wav
/usr/share/games/ppracer/sounds/fish_pickup2.wav
/usr/share/games/ppracer/sounds/tux_on_rock1.wav
/usr/share/games/ppracer/sounds/tux_on_ice1.wav
/usr/share/games/ppracer/sounds/tux_hit_tree1.wav
/usr/share/games/ppracer/sounds/tux_on_snow1.wav
/usr/share/games/ppracer/sounds/fish_pickup3.wav
/usr/share/games/ppracer/tux.tcl
/usr/share/games/ppracer/courses
/usr/share/games/ppracer/courses/themes
/usr/share/games/ppracer/courses/themes/common.tcl
/usr/share/games/ppracer/courses/themes/huds
/usr/share/games/ppracer/courses/themes/huds/common
/usr/share/games/ppracer/courses/themes/huds/common/huds.tcl
/usr/share/games/ppracer/courses/themes/models
/usr/share/games/ppracer/courses/themes/models/stuff
/usr/share/games/ppracer/courses/themes/models/stuff/barrier.png
/usr/share/games/ppracer/courses/themes/models/stuff/barrier.ac
/usr/share/games/ppracer/courses/themes/models/stuff/models.tcl
/usr/share/games/ppracer/courses/themes/models/common
/usr/share/games/ppracer/courses/themes/models/common/tree.png
/usr/share/games/ppracer/courses/themes/models/common/shrub.ac
/usr/share/games/ppracer/courses/themes/models/common/shrub.png
/usr/share/games/ppracer/courses/themes/models/common/models.tcl
/usr/share/games/ppracer/courses/themes/models/common/tree_barren.png
/usr/share/games/ppracer/courses/themes/models/common/tree_barren.ac
/usr/share/games/ppracer/courses/themes/models/common/tree.ac
/usr/share/games/ppracer/courses/themes/models/trees
/usr/share/games/ppracer/courses/themes/models/trees/models.tcl
/usr/share/games/ppracer/courses/themes/models/trees/tree_xmas.png
/usr/share/games/ppracer/courses/themes/models/trees/tree_xmas.ac
/usr/share/games/ppracer/courses/themes/ppracer.tcl
/usr/share/games/ppracer/courses/themes/items
/usr/share/games/ppracer/courses/themes/items/stuff
/usr/share/games/ppracer/courses/themes/items/stuff/life.png
/usr/share/games/ppracer/courses/themes/items/stuff/items.tcl
/usr/share/games/ppracer/courses/themes/items/flags
/usr/share/games/ppracer/courses/themes/items/flags/flag2.png
/usr/share/games/ppracer/courses/themes/items/flags/items.tcl
/usr/share/games/ppracer/courses/themes/items/common
/usr/share/games/ppracer/courses/themes/items/common/start.png
/usr/share/games/ppracer/courses/themes/items/common/flag.png
/usr/share/games/ppracer/courses/themes/items/common/finish.png
/usr/share/games/ppracer/courses/themes/items/common/herring_standard.png
/usr/share/games/ppracer/courses/themes/items/common/items.tcl
/usr/share/games/ppracer/courses/themes/items/herrings
/usr/share/games/ppracer/courses/themes/items/herrings/herring_red.png
/usr/share/games/ppracer/courses/themes/items/herrings/herring_dead.png
/usr/share/games/ppracer/courses/themes/items/herrings/herring_green.png
/usr/share/games/ppracer/courses/themes/items/herrings/star.png
/usr/share/games/ppracer/courses/themes/items/herrings/items.tcl
/usr/share/games/ppracer/courses/themes/terrains
/usr/share/games/ppracer/courses/themes/terrains/common
/usr/share/games/ppracer/courses/themes/terrains/common/ice.png
/usr/share/games/ppracer/courses/themes/terrains/common/buttstart.png
/usr/share/games/ppracer/courses/themes/terrains/common/buttstop.png
/usr/share/games/ppracer/courses/themes/terrains/common/rock.png
/usr/share/games/ppracer/courses/themes/terrains/common/snowparticles.png
/usr/share/games/ppracer/courses/themes/terrains/common/snow.png
/usr/share/games/ppracer/courses/themes/terrains/common/terrains.tcl
/usr/share/games/ppracer/courses/themes/terrains/common/buttprint.png
/usr/share/games/ppracer/courses/themes/terrains/add
/usr/share/games/ppracer/courses/themes/terrains/add/speed.png
/usr/share/games/ppracer/courses/themes/terrains/add/terrains.tcl
/usr/share/games/ppracer/courses/themes/terrains/add/road.png
/usr/share/games/ppracer/courses/themes/terrains/lava
/usr/share/games/ppracer/courses/themes/terrains/lava/lava.png
/usr/share/games/ppracer/courses/themes/terrains/lava/lavastone.png
/usr/share/games/ppracer/courses/themes/terrains/lava/terrains.tcl
/usr/share/games/ppracer/courses/themes/terrains/rock
/usr/share/games/ppracer/courses/themes/terrains/rock/snowyrock.png
/usr/share/games/ppracer/courses/themes/terrains/rock/terrains.tcl
/usr/share/games/ppracer/courses/themes/terrains/ice
/usr/share/games/ppracer/courses/themes/terrains/ice/hardice.png
/usr/share/games/ppracer/courses/themes/terrains/ice/greenice.png
/usr/share/games/ppracer/courses/themes/terrains/ice/terrains.tcl
/usr/share/games/ppracer/courses/themes/terrains/mud
/usr/share/games/ppracer/courses/themes/terrains/mud/mud.png
/usr/share/games/ppracer/courses/themes/terrains/mud/mudstart.png
/usr/share/games/ppracer/courses/themes/terrains/mud/mudprint.png
/usr/share/games/ppracer/courses/themes/terrains/mud/mudparticles.png
/usr/share/games/ppracer/courses/themes/terrains/mud/mudstop.png
/usr/share/games/ppracer/courses/themes/terrains/mud/terrains.tcl
/usr/share/games/ppracer/courses/themes/terrains/sand
/usr/share/games/ppracer/courses/themes/terrains/sand/sand.png
/usr/share/games/ppracer/courses/themes/terrains/sand/redsand.png
/usr/share/games/ppracer/courses/themes/terrains/sand/terrains.tcl
/usr/share/games/ppracer/courses/themes/terrains/snow
/usr/share/games/ppracer/courses/themes/terrains/snow/dsnow2.png
/usr/share/games/ppracer/courses/themes/terrains/snow/snowygrass.png
/usr/share/games/ppracer/courses/themes/terrains/snow/buttstart.png
/usr/share/games/ppracer/courses/themes/terrains/snow/buttstop.png
/usr/share/games/ppracer/courses/themes/terrains/snow/stsnow1.png
/usr/share/games/ppracer/courses/themes/terrains/snow/snowparticles.png
/usr/share/games/ppracer/courses/themes/terrains/snow/dirtsnow.png
/usr/share/games/ppracer/courses/themes/terrains/snow/terrains.tcl
/usr/share/games/ppracer/courses/themes/terrains/snow/stsnow2.png
/usr/share/games/ppracer/courses/themes/terrains/snow/buttprint.png
/usr/share/games/ppracer/courses/themes/terrains/snow/dsnow.png
/usr/share/games/ppracer/courses/themes/terrains/snow/dirtsnowparticles.png
/usr/share/games/ppracer/courses/themes/conditions
/usr/share/games/ppracer/courses/themes/conditions/common
/usr/share/games/ppracer/courses/themes/conditions/common/sunnybottom.png
/usr/share/games/ppracer/courses/themes/conditions/common/nightbottom.png
/usr/share/games/ppracer/courses/themes/conditions/common/nightenv.png
/usr/share/games/ppracer/courses/themes/conditions/common/cloudyright.png
/usr/share/games/ppracer/courses/themes/conditions/common/sunnyright.png
/usr/share/games/ppracer/courses/themes/conditions/common/cloudyleft.png
/usr/share/games/ppracer/courses/themes/conditions/common/sunnyback.png
/usr/share/games/ppracer/courses/themes/conditions/common/eveningback.png
/usr/share/games/ppracer/courses/themes/conditions/common/cloudyback.png
/usr/share/games/ppracer/courses/themes/conditions/common/nightback.png
/usr/share/games/ppracer/courses/themes/conditions/common/cloudybottom.png
/usr/share/games/ppracer/courses/themes/conditions/common/nightfront.png
/usr/share/games/ppracer/courses/themes/conditions/common/envmap.png
/usr/share/games/ppracer/courses/themes/conditions/common/foggy_light.tcl
/usr/share/games/ppracer/courses/themes/conditions/common/conditions.tcl
/usr/share/games/ppracer/courses/themes/conditions/common/eveningfront.png
/usr/share/games/ppracer/courses/themes/conditions/common/nightright.png
/usr/share/games/ppracer/courses/themes/conditions/common/nighttop.png
/usr/share/games/ppracer/courses/themes/conditions/common/cloudyfront.png
/usr/share/games/ppracer/courses/themes/conditions/common/sunnytop.png
/usr/share/games/ppracer/courses/themes/conditions/common/sunnyleft.png
/usr/share/games/ppracer/courses/themes/conditions/common/evening_light.tcl
/usr/share/games/ppracer/courses/themes/conditions/common/eveningenv.png
/usr/share/games/ppracer/courses/themes/conditions/common/nightleft.png
/usr/share/games/ppracer/courses/themes/conditions/common/eveningright.png
/usr/share/games/ppracer/courses/themes/conditions/common/eveningbottom.png
/usr/share/games/ppracer/courses/themes/conditions/common/night_light.tcl
/usr/share/games/ppracer/courses/themes/conditions/common/sunnyfront.png
/usr/share/games/ppracer/courses/themes/conditions/common/cloudytop.png
/usr/share/games/ppracer/courses/themes/conditions/common/eveningleft.png
/usr/share/games/ppracer/courses/themes/conditions/common/eveningtop.png
/usr/share/games/ppracer/courses/themes/conditions/common/sunny_light.tcl
/usr/share/games/ppracer/courses/course_idx.tcl
/usr/share/games/ppracer/courses/events
/usr/share/games/ppracer/courses/events/herring_run
/usr/share/games/ppracer/courses/events/herring_run/bunny_hill
/usr/share/games/ppracer/courses/events/herring_run/bunny_hill/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/bunny_hill/preview.png
/usr/share/games/ppracer/courses/events/herring_run/bunny_hill/elev.png
/usr/share/games/ppracer/courses/events/herring_run/bunny_hill/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/bunny_hill/trees.png
/usr/share/games/ppracer/courses/events/herring_run/snow_valley
/usr/share/games/ppracer/courses/events/herring_run/snow_valley/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/snow_valley/preview.png
/usr/share/games/ppracer/courses/events/herring_run/snow_valley/elev.png
/usr/share/games/ppracer/courses/events/herring_run/snow_valley/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/snow_valley/trees.png
/usr/share/games/ppracer/courses/events/herring_run/twisty_slope
/usr/share/games/ppracer/courses/events/herring_run/twisty_slope/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/twisty_slope/preview.png
/usr/share/games/ppracer/courses/events/herring_run/twisty_slope/elev.png
/usr/share/games/ppracer/courses/events/herring_run/twisty_slope/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/twisty_slope/trees.png
/usr/share/games/ppracer/courses/events/herring_run/tux-toboggan_run
/usr/share/games/ppracer/courses/events/herring_run/tux-toboggan_run/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/tux-toboggan_run/preview.png
/usr/share/games/ppracer/courses/events/herring_run/tux-toboggan_run/elev.png
/usr/share/games/ppracer/courses/events/herring_run/tux-toboggan_run/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/tux-toboggan_run/trees.png
/usr/share/games/ppracer/courses/events/herring_run/hamburger_hill
/usr/share/games/ppracer/courses/events/herring_run/hamburger_hill/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/hamburger_hill/preview.png
/usr/share/games/ppracer/courses/events/herring_run/hamburger_hill/elev.png
/usr/share/games/ppracer/courses/events/herring_run/hamburger_hill/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/hamburger_hill/trees.png
/usr/share/games/ppracer/courses/events/herring_run/herringrunicon.png
/usr/share/games/ppracer/courses/events/herring_run/bumpy_ride
/usr/share/games/ppracer/courses/events/herring_run/bumpy_ride/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/bumpy_ride/preview.png
/usr/share/games/ppracer/courses/events/herring_run/bumpy_ride/elev.png
/usr/share/games/ppracer/courses/events/herring_run/bumpy_ride/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/bumpy_ride/trees.png
/usr/share/games/ppracer/courses/events/herring_run/the_narrow_way
/usr/share/games/ppracer/courses/events/herring_run/the_narrow_way/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/the_narrow_way/preview.png
/usr/share/games/ppracer/courses/events/herring_run/the_narrow_way/elev.png
/usr/share/games/ppracer/courses/events/herring_run/the_narrow_way/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/the_narrow_way/trees.png
/usr/share/games/ppracer/courses/events/herring_run/high_road
/usr/share/games/ppracer/courses/events/herring_run/high_road/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/high_road/preview.png
/usr/share/games/ppracer/courses/events/herring_run/high_road/elev.png
/usr/share/games/ppracer/courses/events/herring_run/high_road/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/high_road/trees.png
/usr/share/games/ppracer/courses/events/herring_run/ski_jump
/usr/share/games/ppracer/courses/events/herring_run/ski_jump/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/ski_jump/preview.png
/usr/share/games/ppracer/courses/events/herring_run/ski_jump/elev.png
/usr/share/games/ppracer/courses/events/herring_run/ski_jump/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/ski_jump/trees.png
/usr/share/games/ppracer/courses/events/herring_run/penguins_cant_fly
/usr/share/games/ppracer/courses/events/herring_run/penguins_cant_fly/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/penguins_cant_fly/preview.png
/usr/share/games/ppracer/courses/events/herring_run/penguins_cant_fly/elev.png
/usr/share/games/ppracer/courses/events/herring_run/penguins_cant_fly/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/penguins_cant_fly/trees.png
/usr/share/games/ppracer/courses/events/herring_run/cupicon.png
/usr/share/games/ppracer/courses/events/herring_run/path_of_daggers
/usr/share/games/ppracer/courses/events/herring_run/path_of_daggers/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/path_of_daggers/preview.png
/usr/share/games/ppracer/courses/events/herring_run/path_of_daggers/elev.png
/usr/share/games/ppracer/courses/events/herring_run/path_of_daggers/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/path_of_daggers/trees.png
/usr/share/games/ppracer/courses/events/herring_run/mount_satan
/usr/share/games/ppracer/courses/events/herring_run/mount_satan/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/mount_satan/preview.png
/usr/share/games/ppracer/courses/events/herring_run/mount_satan/elev.png
/usr/share/games/ppracer/courses/events/herring_run/mount_satan/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/mount_satan/trees.png
/usr/share/games/ppracer/courses/events/herring_run/mount_herring
/usr/share/games/ppracer/courses/events/herring_run/mount_herring/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/mount_herring/preview.png
/usr/share/games/ppracer/courses/events/herring_run/mount_herring/elev.png
/usr/share/games/ppracer/courses/events/herring_run/mount_herring/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/mount_herring/trees.png
/usr/share/games/ppracer/courses/events/herring_run/ive_got_a_woody
/usr/share/games/ppracer/courses/events/herring_run/ive_got_a_woody/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/ive_got_a_woody/preview.png
/usr/share/games/ppracer/courses/events/herring_run/ive_got_a_woody/elev.png
/usr/share/games/ppracer/courses/events/herring_run/ive_got_a_woody/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/ive_got_a_woody/trees.png
/usr/share/games/ppracer/courses/events/herring_run/deadman
/usr/share/games/ppracer/courses/events/herring_run/deadman/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/deadman/preview.png
/usr/share/games/ppracer/courses/events/herring_run/deadman/elev.png
/usr/share/games/ppracer/courses/events/herring_run/deadman/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/deadman/trees.png
/usr/share/games/ppracer/courses/events/herring_run/skull_mountain
/usr/share/games/ppracer/courses/events/herring_run/skull_mountain/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/skull_mountain/preview.png
/usr/share/games/ppracer/courses/events/herring_run/skull_mountain/elev.png
/usr/share/games/ppracer/courses/events/herring_run/skull_mountain/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/skull_mountain/trees.png
/usr/share/games/ppracer/courses/events/herring_run/hazzard_valley
/usr/share/games/ppracer/courses/events/herring_run/hazzard_valley/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/hazzard_valley/preview.png
/usr/share/games/ppracer/courses/events/herring_run/hazzard_valley/elev.png
/usr/share/games/ppracer/courses/events/herring_run/hazzard_valley/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/hazzard_valley/trees.png
/usr/share/games/ppracer/courses/events/herring_run/ice_labyrinth
/usr/share/games/ppracer/courses/events/herring_run/ice_labyrinth/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/ice_labyrinth/preview.png
/usr/share/games/ppracer/courses/events/herring_run/ice_labyrinth/elev.png
/usr/share/games/ppracer/courses/events/herring_run/ice_labyrinth/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/ice_labyrinth/trees.png
/usr/share/games/ppracer/courses/events/herring_run/keep_it_up
/usr/share/games/ppracer/courses/events/herring_run/keep_it_up/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/keep_it_up/preview.png
/usr/share/games/ppracer/courses/events/herring_run/keep_it_up/elev.png
/usr/share/games/ppracer/courses/events/herring_run/keep_it_up/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/keep_it_up/trees.png
/usr/share/games/ppracer/courses/events/herring_run/frozen_river
/usr/share/games/ppracer/courses/events/herring_run/frozen_river/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/frozen_river/preview.png
/usr/share/games/ppracer/courses/events/herring_run/frozen_river/elev.png
/usr/share/games/ppracer/courses/events/herring_run/frozen_river/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/frozen_river/trees.png
/usr/share/games/ppracer/courses/events/herring_run/slalom
/usr/share/games/ppracer/courses/events/herring_run/slalom/terrain.png
/usr/share/games/ppracer/courses/events/herring_run/slalom/preview.png
/usr/share/games/ppracer/courses/events/herring_run/slalom/elev.png
/usr/share/games/ppracer/courses/events/herring_run/slalom/course.tcl
/usr/share/games/ppracer/courses/events/herring_run/slalom/trees.png
/usr/share/games/ppracer/courses/events/herring_run/event.tcl
/usr/share/games/ppracer/courses/contrib
/usr/share/games/ppracer/courses/contrib/doing
/usr/share/games/ppracer/courses/contrib/doing/terrain.png
/usr/share/games/ppracer/courses/contrib/doing/preview.png
/usr/share/games/ppracer/courses/contrib/doing/elev.png
/usr/share/games/ppracer/courses/contrib/doing/course.tcl
/usr/share/games/ppracer/courses/contrib/doing/trees.png
/usr/share/games/ppracer/ppracer_init.tcl
/usr/share/games/ppracer/translations
/usr/share/games/ppracer/translations/fr_FR.tcl
/usr/share/games/ppracer/translations/eu_ES.tcl
/usr/share/games/ppracer/translations/pt_PT.tcl
/usr/share/games/ppracer/translations/nl_NL.tcl
/usr/share/games/ppracer/translations/es_ES.tcl
/usr/share/games/ppracer/translations/nn_NO.tcl
/usr/share/games/ppracer/translations/nb_NO.tcl
/usr/share/games/ppracer/translations/it_IT.tcl
/usr/share/games/ppracer/translations/de_DE.tcl
/usr/share/games/ppracer/translations/ru_RU.tcl
/usr/share/games/ppracer/translations/en_GB.tcl
/usr/share/games/ppracer/translations/languages.tcl
/usr/share/games/ppracer/music
/usr/share/games/ppracer/music/start1-jt.it
/usr/share/games/ppracer/music/options1-jt.it
/usr/share/games/ppracer/music/race2-jt.it
/usr/share/games/ppracer/music/wonrace1-jt.it
/usr/share/games/ppracer/music/race1-jt.it
/usr/share/app-install/icons/ppracer-128x128.png
/usr/share/app-install/desktop/ppracer.desktop
/usr/share/man/man6/ppracer.6.gz
/usr/share/man/de/man6/ppracer.6.gz
/home/the8thstar/.ppracer
/home/the8thstar/.ppracer/tux.sav
/home/the8thstar/.ppracer/options
/var/lib/gnome/Debian/Games/Arcade/ppracer.desktop
/var/lib/menu-xdg/applications/menu-xdg/X-Debian-Games-Arcade-ppracer.desktop


---

### Post by taurus on 2007-05-26
The game is in /usr/games/ppracer, _not_ /root/usr/games/ppracer.

```
/usr/games/ppracer
```

---

### Post by the8thstar on 2007-05-27
Okay... :???: But I still don't know what to do. Can someone help?

---

### Post by RomeReactor on 2007-05-27
Hi. Running it from the terminal like this:
```
/usr/games/ppracer
```
didn't launch the game? does the terminal show any errors?

---

### Post by the8thstar on 2007-06-02
In the terminal (with root privileges) the command /usr/games/ppracer doesn't work. I literally have to drag the ppracer icon located in /usr/games and drop it into the terminal, follwed by Enter to make it work! What is wrong here?

---

### Post by the8thstar on 2007-06-04
Ha, I think even the tech wiz have no clue about this one! :P

---

### Post by Bachstelze on 2007-06-04
If you're trying to run the game with root privileges, it's nomal it doesn't work. Run it as yourself

---

### Post by the8thstar on 2007-06-04
And this is just my problem... it won't run under my username. At all.

---

### Post by the8thstar on 2007-06-17
I found a way to ease things out a bit. It still requires that I input my password, but here goes:

> gksudo '/usr/games/ppracer' is what I put in the properties tab of the launcher. It's better than nothing.

---

