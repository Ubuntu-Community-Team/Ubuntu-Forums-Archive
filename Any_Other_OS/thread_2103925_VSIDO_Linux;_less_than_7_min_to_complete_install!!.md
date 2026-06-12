---
title: "VSIDO Linux; less than 7 min to complete install!!!"
date: 2013-01-11
forum: Any Other OS
---

### Post by Jedcurtis on 2013-01-11
VastOne, amazing as always!  VSIDO is totally awesome.  Here is a scrot of the install completing in less than 7 minutes!  [[img]http://www.zimagez.com/miniature/screenshot-01112013-010730pm.png[/img]](http://www.zimagez.com/zimage/screenshot-01112013-010730pm.php)

---

### Post by Haghiri75 on 2013-01-11
> **Jedcurtis said:**
> VastOne, amazing as always!  VSIDO is totally awesome.  Here is a scrot of the install completing in less than 7 minutes!  [[img]http://www.zimagez.com/miniature/screenshot-01112013-010730pm.png[/img]](http://www.zimagez.com/zimage/screenshot-01112013-010730pm.php)
&#1617;Is it Independent ? or Based on other distros?

---

### Post by Habitual on 2013-01-11
Rockin' Conky work!
[http://www.jedsdesk.com/wp-content/uploads/2012/12/desktop9.jpg](http://www.jedsdesk.com/wp-content/uploads/2012/12/desktop9.jpg)

How cool is this?...This is what happens when you learn how to &#8220;[COLOR=blue]Ctrl-C and Ctrl-V[/COLOR]&#8220;! (maybe a little [COLOR=blue]Ctrl-X[/COLOR] as well!) 

I'd love to have that setup, or some/most of it.

---

### Post by y6FgBn)~v on 2013-01-11
> **Habitual said:**
> Rockin' Conky work!
[http://www.jedsdesk.com/wp-content/uploads/2012/12/desktop9.jpg](http://www.jedsdesk.com/wp-content/uploads/2012/12/desktop9.jpg)

How cool is this?...This is what happens when you learn how to “[COLOR=blue]Ctrl-C and Ctrl-V[/COLOR]“! (maybe a little [COLOR=blue]Ctrl-X[/COLOR] as well!) 

I'd love to have that setup, or some/most of it.

Kick Monkey Kick!!! ):P

---

### Post by Jedcurtis on 2013-01-11
Thanks for the kind words folks!!!  This distro is based on Debian (as is Ubuntu) and is created by a fella here on the forums and also on the Crunchbang forums named VastOne.  His distro is brilliant work.  I've been testing it since Nov. 11th.  I think it'll go "live" next week at some point.  I'll be posting updates about it on my website jedsdesk.com.  The Conky work is simply cut and paste stuff!!!  If anyone wants any of it just let me know.  Obviously you'd have to change some settings to conform to your particular setup but if I can do it anyone can!  Here's my current desktop using VSIDO Linux....
[[img]http://www.zimagez.com/miniature/screenshot-01112013-033225pm.png[/img]](http://www.zimagez.com/zimage/screenshot-01112013-033225pm.php)

Jed :mrgreen:

---

### Post by lwfitz on 2013-01-11
Nice work Jed! VastOne's a genius for sure! VSIDO has been tested on all kinds of hardware with almost no real issues at all. This includes SSD's, hybrid graphics, AMD/ATI cpu/gpu, older 64bit cpus(pentium D and 3rd generation P4) and much more. 

[[img]http://ompldr.org/tZ3lvMw[/img]](http://ompldr.org/vZ3lvMw)

[[img]http://ompldr.org/taDEwdQ[/img]](http://ompldr.org/vaDEwdQ)

---

### Post by Habitual on 2013-01-11
> **pcybill said:**
> Kick Monkey Kick!!! ):P

Spawn!

so much more is possible with MrPeachy's LUA alchemy.

---

### Post by Habitual on 2013-01-11
> **Jedcurtis said:**
> ...If anyone wants any of it just let me know....Jed :mrgreen:

Jed: You have conkrc/LUAs for [http://www.jedsdesk.com/wp-content/uploads/2012/12/desktop9.jpg](http://www.jedsdesk.com/wp-content/uploads/2012/12/desktop9.jpg) ?

conky code hacking requirement acknowledged. ;)

---

### Post by Jedcurtis on 2013-01-11
> **Habitual said:**
> Jed: You have conkrc/LUAs for [http://www.jedsdesk.com/wp-content/uploads/2012/12/desktop9.jpg](http://www.jedsdesk.com/wp-content/uploads/2012/12/desktop9.jpg) ?

conky code hacking requirement acknowledged. ;)

Yes, I do.  However, there are I think, 6 different Conkys on that desktop.  It was just an example as we were playing with the testing version of VSIDO.  If you point out the one you want, I'm sure I can dig it out for you.

All of the Conky's are the work of Conky Masters, which I ain't.  The cut/paste comment is the utter truth!!! :D  Well, OK, I may know a little more than cut/paste...
Let me know.

Jed

---

### Post by Habitual on 2013-01-11
> **Jedcurtis said:**
> Yes, I do.  However, there are I think, 6 different Conkys on that desktop.  It was just an example as we were playing with the testing version of VSIDO.  If you point out the one you want, I'm sure I can dig it out for you.

All of the Conky's are the work of Conky Masters, which I ain't.  The cut/paste comment is the utter truth!!! :D  Well, OK, I may know a little more than cut/paste...
Let me know.

Jed

[Here's my last conky.fu]("http://i771.photobucket.com/albums/xx360/E522260/desktop_9_21_2010.png") 
About 10 little conkyrcs altogether. 
All done by hand from scratch.
Any Conky Masters' work I may receive will *not *be wasted.

See attached for my request.
Just the face and contents of it. 

Thank you.

---

### Post by lwfitz on 2013-01-11
> **Habitual said:**
> [Here's my last conky.fu]("http://i771.photobucket.com/albums/xx360/E522260/desktop_9_21_2010.png") 
About 10 little conkyrcs altogether. 
All done by hand from scratch.
Any Conky Masters' work I may receive will *not *be wasted.

See attached for my request.
Just the face and contents of it. 

Thank you.


Wow! Looks fantastic Habitual!

---

### Post by Jedcurtis on 2013-01-11
That is an incredible layout you've got there with your Conky's!!!

OK, here you go!

One thing to note;  If you don't have mrpeachy's v9000 weather script, the weather portion wont work.

greyclock_conkyrc
```
# &#8212; Conky settings &#8212; #

background yes

update_interval 1
total_run_times 0
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
imlib_cache_size 0


# &#8212; Window specifications &#8212; #
own_window_type normal
own_window_class Conky
own_window yes
#own_window_type conky
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

border_inner_margin 0
border_outer_margin 0

minimum_size 600 700
maximum_width 600

alignment top_middle

gap_x 0
gap_y 50



# &#8212; Graphics settings &#8212; #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# &#8212; Text settings &#8212; #
use_xft yes
xftfont LCDMono2:size=10.1
xftalpha 1.0

default_color 227992 ##dark red A84C47 ##opaque white FFFFFF

uppercase no
use_spacer right

# &#8212; Lua Load &#8212; #
lua_load ~/conky/greyclock/greyclock.lua
lua_draw_hook_post main
lua_load ~/v9000/v9000.lua
lua_draw_hook_pre weather
lua_load ~/conky/greyclock/chrono-full.template.lua


TEXT
${voffset 305}${goto 290}${font LCDMono2:size=23.1}${time %l:%M}${font}
${voffset 2}${goto 292}${time %a %d %b}  









```greyclock.lua

```
require 'cairo'
--------------------------------------------------------------------------------
----Adjustable Settings 
coffee_table = {
    {
    name='time',                   arg='%I.%M',                    max_value=12,
    x=230,                         y=230,
    cup_radius=112, --hour-hand
    cup_wall_thickness=90,
    cup_bg_clr=0xffffff,           cup_bg_alpha=0.0,
    cup_fg_clr=0xFFFFFF,           cup_fg_alpha=0.0,
    handle_length=70,              handle_circ=5,
    handle_fg_clr=0xFFFFFF,        handle_fg_alpha=1.0,
    graduation_radius=184,
    graduation_thickness=8,        graduation_mark_circ=1.5,
    graduation_mark_angle=30,
    graduation_fg_clr=0xFFFFFF,    graduation_fg_alpha=0.5,
    saucer_thickness=6,            thick_saucer_circ=11/12,    
    saucer_radius=195,             thin_saucer_circ=11/12,    
    saucer_fg_clr=0xFFFFFF,        saucer_fg_alpha=0.3, 
    saucer_mark_fg_clr=0xFFFFFF,   saucer_mark_fg_alpha=0.0,
    inner_saucer=true, 
    txt_weight=0,                  txt_size=8.0,
    txt_fg_clr=0xFFFFFF,           txt_fg_alpha=0.0,
    caption='',                    caption2='',
    },
   {
    name='time',                   arg='%H',                    max_value=12,
    x=230,                         y=230,
    cup_radius=2,
    cup_wall_thickness=3,
    cup_bg_clr=0xffffff,           cup_bg_alpha=1.0,
    cup_fg_clr=0xFFFFFF,           cup_fg_alpha=1.0,
    handle_length=40,              handle_circ=4,
    handle_fg_clr=0xFFFFFF,        handle_fg_alpha=0.0,
    graduation_radius=187,
    graduation_thickness=1,        graduation_mark_circ=0.5,
    graduation_mark_angle=3,
    graduation_fg_clr=0xFFFFFF,    graduation_fg_alpha=0.5,
    saucer_thickness=6,            thick_saucer_circ=11/12,    
    saucer_radius=195,             thin_saucer_circ=11/12,    
    saucer_fg_clr=0xFFFFFF,        saucer_fg_alpha=0.0, 
    saucer_mark_fg_clr=0xFFFFFF,   saucer_mark_fg_alpha=0.0,
    inner_saucer=true, 
    txt_weight=0,                  txt_size=8.0,
    txt_fg_clr=0xFFFFFF,           txt_fg_alpha=0.0,
    caption='',                    caption2='',
    },
    {
    name='time',                   arg='%M',                    max_value=60,
    x=230,                         y=230,
    cup_radius=118,
    cup_wall_thickness=120,
    cup_bg_clr=0xffffff,           cup_bg_alpha=0.0,
    cup_fg_clr=0xFFFFFF,           cup_fg_alpha=0.0,
    graduation_radius=183,
    graduation_thickness=10,       graduation_mark_circ=2.5,
    graduation_mark_angle=90,
    graduation_fg_clr=0xFFFFFF,    graduation_fg_alpha=0.5,
    handle_length=110,              handle_circ=3,
    handle_fg_clr=0xFFFFFF,        handle_fg_alpha=1.0,
    saucer_thickness=6,            thick_saucer_circ=11/12,
    saucer_radius=220,             thin_saucer_circ=11/12,    
    saucer_fg_clr=0xFFFFFF,        saucer_fg_alpha=0.3,
    saucer_mark_fg_clr=0xFFFFFF,   saucer_mark_fg_alpha=0.0,
    txt_weight=0,                  txt_size=8.0,
    txt_fg_clr=0xFFFFFF,           txt_fg_alpha=0.0,
    caption='',                    caption2='',
    },
    {
    name='time',                   arg='%S',                    max_value=60,
    x=230,                         y=230,
    cup_radius=120,
    cup_wall_thickness=120,
    cup_bg_clr=0xffffff,           cup_bg_alpha=0.0,
    cup_fg_clr=0xFFFFFF,             cup_fg_alpha=0.0,
    handle_fg_clr=0xFFFFFF,        handle_fg_alpha=1.0,
    handle_length=118,              handle_circ=1,
    graduation_radius=185,
    graduation_thickness=6,        graduation_mark_circ=0.5,
    graduation_mark_angle=6,
    graduation_fg_clr=0xFFFFFF,    graduation_fg_alpha=0.5,
    saucer_thickness=5,           thick_saucer_circ=1,
    saucer_radius=205,             thin_saucer_circ=11/12,    
    saucer_fg_clr=0xFFFFFF,        saucer_fg_alpha=0.4,
    saucer_mark_fg_clr=0xFFFFFF,   saucer_mark_fg_alpha=0.4,
    txt_weight=0,                  txt_size=8.0,
    txt_fg_clr=0xFFFFFF,           txt_fg_alpha=0.0,
    caption='',                    caption2='',
},

    {
    name='cpu',                    arg='cpu0',                  max_value=100,
    x=230,                         y=105,
    cup_radius=20,
    cup_wall_thickness=40,
    cup_start_angle=0,
    cup_bg_clr=0xFFFFFF,           cup_bg_alpha=0.0,
    cup_fg_clr=0xFFFFFF,           cup_fg_alpha=0.0,
    handle_fg_clr=0xFFFFFF,        handle_fg_alpha=0.0,
    handle_length=40,              handle_circ=4,
    xtxt=-20,               ytxt= -12,
    txt_weight=0,                  txt_size=10.0,
    txt_fg_clr=0xFFFFFF,           txt_fg_alpha=0.8,
    caption='CPU ',               caption2=' %',
    graduation_radius=35,
    graduation_thickness=3,        graduation_mark_circ=2,
    graduation_mark_angle=36,
    graduation_fg_clr=0xFFFFFF,    graduation_fg_alpha=0.6,
    saucer_thickness=6,            thick_saucer_circ=0.85,
    saucer_radius=40,              thin_saucer_circ=0.85,
    saucer_fg_clr=0xFFFFFF,       saucer_fg_alpha= 0.3,
    saucer_mark_fg_clr=0xFFFFFF,   saucer_mark_fg_alpha=0.5,
    inner_saucer=true,
    },
    {
    name='freq_g',                 arg='/',                  max_value=5,
    x=230,                         y=105,
    cup_radius=12,
    cup_wall_thickness=23,
    cup_start_angle=0,
    cup_bg_clr=0xFFFFFF,           cup_bg_alpha=0.0,
    cup_fg_clr=0xFFFFFF,           cup_fg_alpha=0.0,
    handle_fg_clr=0xFFFFFF,        handle_fg_alpha=0.0,
    handle_length=40,              handle_circ=4,
    xtxt=-20,               ytxt= 0,
    txt_weight=0,                  txt_size=10.0,
    txt_fg_clr=0xFFFFFF,           txt_fg_alpha=0.8,
    caption='',           caption2=' GHz',
    graduation_radius=25,
    graduation_thickness=6,        graduation_mark_circ=4,
    graduation_mark_angle=30,
    graduation_fg_clr=0xFFFFFF,    graduation_fg_alpha=0.0,
    saucer_thickness=6,            thick_saucer_circ=0.75,
    saucer_radius=45,              thin_saucer_circ=0.75,
    saucer_fg_clr=0xFFFFFF,       saucer_fg_alpha= 0.3,
    saucer_mark_fg_clr=0xFFFFFF,   saucer_mark_fg_alpha=0.5,
},
{
    name='hwmon',                arg='temp 1',                      max_value=100,
    x=230,                         y=105,
    cup_radius=12,
    cup_wall_thickness=23,
    cup_start_angle=0,
    cup_bg_clr=0xFFFFFF,           cup_bg_alpha=0.0,
    cup_fg_clr=0xFFFFFF,           cup_fg_alpha=0.0,
    handle_fg_clr=0xFFFFFF,        handle_fg_alpha=0.0,
    handle_length=40,              handle_circ=4,
    xtxt=-15,               ytxt= 12,
    txt_weight=0,                  txt_size=10.0,
    txt_fg_clr=0xFFFFFF,           txt_fg_alpha=0.8,
    caption='',             caption2=' ºC',
    graduation_radius=35,
    graduation_thickness=6,        graduation_mark_circ=2,
    graduation_mark_angle=36,
    graduation_fg_clr=0xFFFFFF,    graduation_fg_alpha=0.6,
    saucer_thickness=6,           thick_saucer_circ=0.85,
    saucer_radius=40,              thin_saucer_circ=0.85,    
    saucer_fg_clr=0xFFFFFF,        saucer_fg_alpha= 0.3,
    saucer_mark_fg_clr=0xFFFFFF,   saucer_mark_fg_alpha=0.5,
    inner_saucer=true,
},   
---------------1/2
{
    name='memperc',                arg='/',                      max_value=100,
    x=135,                         y=150,
    cup_radius=12,
    cup_wall_thickness=23,
    cup_start_angle=0,
    cup_bg_clr=0xFFFFFF,           cup_bg_alpha=0.0,
    cup_fg_clr=0xFFFFFF,           cup_fg_alpha=0.0,
    handle_fg_clr=0xFFFFFF,        handle_fg_alpha=0.0,
    handle_length=40,              handle_circ=4,
    xtxt=-25,               ytxt=0,
    txt_weight=0,                  txt_size=10.0,
    txt_fg_clr=0xFFFFFF,           txt_fg_alpha=0.8,
    caption='RAM ',             caption2=' %',
    graduation_radius=35,
    graduation_thickness=6,        graduation_mark_circ=2,
    graduation_mark_angle=36,
    graduation_fg_clr=0xFFFFFF,    graduation_fg_alpha=0.6,
    saucer_thickness=6,           thick_saucer_circ=0.85,
    saucer_radius=40,              thin_saucer_circ=0.85,    
    saucer_fg_clr=0xFFFFFF,        saucer_fg_alpha= 0.3,
    saucer_mark_fg_clr=0xFFFFFF,   saucer_mark_fg_alpha=0.5,
    inner_saucer=true,
},   
------------------2/3    
{
    name='fs_used_perc',           arg='/home',                      max_value=100,
    x=105,                         y=240,
    cup_radius=12,
    cup_wall_thickness=27,
    cup_start_angle=0,
    cup_bg_clr=0xFFFFFF,           cup_bg_alpha=0.0,
    cup_fg_clr=0xFFFFFF,           cup_fg_alpha=0.0,
    handle_fg_clr=0xFFFFFF,        handle_fg_alpha=0.0,
    handle_length=40,              handle_circ=4,
    xtxt=-30,               ytxt= 12,
    txt_weight=0,                  txt_size=10.0,
    txt_fg_clr=0xFFFFFF,           txt_fg_alpha=0.8,
    caption=' FS H: ',             caption2=' %',
    graduation_radius=35,
    graduation_thickness=6,        graduation_mark_circ=2,
    graduation_mark_angle=36,
    graduation_fg_clr=0xFFFFFF,    graduation_fg_alpha=0.6,    
    saucer_thickness=6,            thick_saucer_circ=0.85,
    saucer_radius=40,              thin_saucer_circ=0.85,     
    saucer_fg_clr=0xFFFFFF,        saucer_fg_alpha=0.3,
    saucer_mark_fg_clr=0xFFFFFF,   saucer_mark_fg_alpha=0.5,
    inner_saucer=true,
},
{
    name='fs_used_perc',           arg='/',                      max_value=100,
    x=105,                         y=240,
    cup_radius=12,
    cup_wall_thickness=27,
    cup_start_angle=0,
    cup_bg_clr=0xFFFFFF,           cup_bg_alpha=0.0,
    cup_fg_clr=0xFFFFFF,           cup_fg_alpha=0.0,
    handle_fg_clr=0xFFFFFF,        handle_fg_alpha=0.0,
    handle_length=40,              handle_circ=4,
    xtxt=-30,               ytxt= -5,
    txt_weight=0,                  txt_size=10.0,
    txt_fg_clr=0xFFFFFF,           txt_fg_alpha=0.8,
    caption=' FS /: ',             caption2=' %',
    graduation_radius=25,
    graduation_thickness=4,        graduation_mark_circ=4,
    graduation_mark_angle=36,
    graduation_fg_clr=0xFFFFFF,    graduation_fg_alpha=0.0,
    saucer_thickness=6,            thick_saucer_circ=0.85,
    saucer_radius=45,              thin_saucer_circ=0.85,     
    saucer_fg_clr=0xFFFFFF,        saucer_fg_alpha=0.3,
    saucer_mark_fg_clr=0xFFFFFF,   saucer_mark_fg_alpha=0.5,
},
}
  
--Fixed code -do not edit unless you know what you are doing------------------------------------------------------------------------
-------------------------------------------------------------------------------
-- converts color in hexa to decimal
function rgb_to_r_g_b(clr, alpha)
    return ((clr / 0x10000) % 0x100) / 255., ((clr / 0x100) % 0x100) / 255., (clr % 0x100) / 255., alpha
end
-------------------------------------------------------------------------------
------------------------------------------------------------------------
local function draw_coffee_table(display, data, value) 
     max_value = data['max_value']
     x, y = data['x'], data['y']
     if x==nil then x=conky_window.width/2 end
     if y==nil then y=conky_window.height/2 end    
     cup_radius = data['cup_radius']    
     if cup_radius==nil then cup_radius=conky_window.width/4 end    
     cup_wall_thickness = data['cup_wall_thickness']
     if cup_wall_thickness==nil then cup_wall_thickness=20 end
     handle_length, handle_circ = data['handle_length'], data['handle_circ']
     if handle_length==nil then handle_length=20 end
     if handle_circ==nil then handle_circ=1 end
     cup_start_angle = data['cup_start_angle']
     if cup_start_angle == nil then cup_start_angle =0 end
     total_angle = data['total_angle']
     if total_angle == nil then total_angle=360 end
     cup_sector_angle = (math.abs(total_angle))/max_value  
     cup_end_angle = total_angle + cup_start_angle
     cup_bg_clr, cup_bg_alpha = data['cup_bg_clr'], data['cup_bg_alpha']
     if cup_bg_clr==nil then cup_bg_clr =0xffffff end
     cup_fg_clr, cup_fg_alpha = data['cup_fg_clr'], data['cup_fg_alpha']
     if cup_fg_clr==nil then cup_fg_clr =0xffffff end
     if cup_fg_alpha==nil then cup_fg_alpha=0 end
     handle_fg_clr, handle_fg_alpha = data['handle_fg_clr'], data['handle_fg_alpha']  
     if handle_fg_clr==nil then handle_fg_clr = 0xffffff end
     if handle_fg_alpha==nil then handle_fg_alpha=0 end
     
     saucer_radius = data['saucer_radius']
     if saucer_radius==nil then saucer_radius=conky_window.width/2 end 
     total_saucer_angle=data['total_saucer_angle']
     if total_saucer_angle==nil then total_saucer_angle=360 end 
     saucer_sector_angle=(math.abs(total_saucer_angle))/max_value  
     saucer_thickness = data['saucer_thickness']
     if saucer_thickness==nil then saucer_thickness=6 end
     saucer_fg_clr = data['saucer_fg_clr']
     if saucer_fg_clr ==nil then saucer_fg_clr=0 end
     saucer_fg_alpha = data['saucer_fg_alpha']
     if saucer_fg_alpha ==nil then saucer_fg_alpha=0 end
     
     saucer_mark_fg_alpha = data['saucer_mark_fg_alpha']
     if saucer_mark_fg_alpha ==nil then saucer_mark_fg_alpha=0 end
     saucer_mark_fg_clr = data['saucer_mark_fg_clr']
     if saucer_mark_fg_clr ==nil then saucer_mark_fg_clr=0xffffff end
     thick_saucer_circ = data['thick_saucer_circ']
     if thick_saucer_circ==nil then thick_saucer_circ =0.9 end
     thin_saucer_circ = data['thin_saucer_circ']
     if thin_saucer_circ==nil then thin_saucer_circ =0.9 end
     inner_saucer = data['inner_saucer']
     
     graduation_radius = data['graduation_radius']
     if graduation_radius ==nil then graduation_radius = conky_window.width/3 end
     graduation_thickness, graduation_mark_circ = data['graduation_thickness'], data['graduation_mark_circ']
     if graduation_thickness ==nil then graduation_thickness = 2 end
     if graduation_mark_circ ==nil then graduation_mark_circ = 1 end
     graduation_mark_angle = data['graduation_mark_angle']
     if graduation_mark_angle == nil then graduation_mark_angle = total_angle/10 end
     graduation_fg_clr, graduation_fg_alpha = data['graduation_fg_clr'], data['graduation_fg_alpha']
     if graduation_fg_clr ==nil then graduation_fg_clr= 0xffffff end
     if graduation_fg_alpha==nil then graduation_fg_alpha =0 end
     
     
     txt_weight, txt_size = data['txt_weight'], data['txt_size']
     if txt_weight == nil then txt_weight=1 end
     if txt_size == nil then txt_size=8 end
     txt_fg_clr, txt_fg_alpha = data['txt_fg_clr'], data['txt_fg_alpha']
     if txt_fg_clr ==nil then txt_fg_clr= 0xffffff end
     if txt_fg_alpha==nil then txt_fg_alpha =0 end
     caption = data['caption']
     if caption==nil then caption='' end
     caption2 = data['caption2']
     if caption2==nil then caption2='' end
     xtxt, ytxt= data ['xtxt'], data['ytxt']
     if xtxt ==nil then xtxt=0 end
     if ytxt ==nil then ytxt=0 end

--convert degree to rad and rotate (0 degree is top/north)
    function angle_to_position(start_angle, current_angle)    
      if total_angle < 0 then 
        local pos = start_angle - current_angle
        return ( ( pos * (math.pi / 180) ) - (math.pi / 2) )
      else 
        local pos = current_angle + start_angle 
        return ( ( pos * (math.pi / 180) ) - (math.pi / 2) ) 
      end   
    end
--cup centre background    
  if cup_bg_alpha >0   then
    if total_angle < 0 then
      cairo_arc_negative(display, x, y, cup_radius, angle_to_position(cup_start_angle, 0), angle_to_position(cup_end_angle, 0))
    else
      cairo_arc(display, x, y, cup_radius, angle_to_position(cup_start_angle, 0), angle_to_position(cup_start_angle, cup_end_angle))
    end
    cairo_set_source_rgba(display, rgb_to_r_g_b(cup_bg_clr, cup_bg_alpha))
    cairo_set_line_width(display, cup_wall_thickness)
    cairo_stroke(display)
  end 
--cup wall fg    
  if cup_fg_alpha > 0 then 
   local fg_stop_arc = (cup_sector_angle * value)
    if total_angle < 0 then
    cairo_arc_negative(display, x, y, cup_radius, angle_to_position(cup_start_angle, 0), angle_to_position(cup_start_angle, fg_stop_arc))
    else
    cairo_arc(display, x, y, cup_radius, angle_to_position(cup_start_angle, 0), angle_to_position(cup_start_angle, fg_stop_arc))
    end
    cairo_set_source_rgba(display, rgb_to_r_g_b(cup_fg_clr, cup_fg_alpha))
    cairo_set_line_width(display, cup_wall_thickness)
    cairo_stroke(display)
  end
-- cup handle
  if handle_fg_alpha>0 then 
    local start_handle = (cup_sector_angle * value) - (handle_circ*0.5)
    local stop_handle = (cup_sector_angle * value) +  (handle_circ*0.5)
    if total_angle < 0 then
    cairo_arc_negative(display, x, y, cup_radius, angle_to_position(cup_start_angle, start_handle), angle_to_position(cup_start_angle, stop_handle))
    else
    cairo_arc(display, x, y, cup_radius, angle_to_position(cup_start_angle, start_handle), angle_to_position(cup_start_angle, stop_handle))
    end
    cairo_set_line_width(display, handle_length)    
    cairo_set_source_rgba(display, rgb_to_r_g_b(handle_fg_clr, handle_fg_alpha))
    cairo_stroke(display)
  end
--saucers   
---thick saucer     
    if saucer_fg_alpha > 0 and (thin_saucer_circ >0 or thick_saucer_circ > 0)
      then 
    if value < (max_value/2) 
        then j = value + ((max_value*total_saucer_angle)/720)
        else j = value - ((max_value*total_saucer_angle)/720)
    end
    
    local start_saucer = (saucer_sector_angle * j) - (value*saucer_sector_angle*0.5*thick_saucer_circ)
    local stop_saucer = (saucer_sector_angle * j) + (value*saucer_sector_angle*0.5*thick_saucer_circ)
    if total_angle < 0 then
    cairo_arc_negative(display, x, y, saucer_radius, angle_to_position(cup_start_angle, start_saucer), angle_to_position(cup_start_angle, stop_saucer))
    else
    cairo_arc(display, x, y, saucer_radius, angle_to_position(cup_start_angle, start_saucer), angle_to_position(cup_start_angle, stop_saucer))
    end
    cairo_set_source_rgba(display, rgb_to_r_g_b(saucer_fg_clr, saucer_fg_alpha))
    cairo_set_line_width(display, saucer_thickness)
    cairo_stroke(display)
    --thin saucer
      if inner_saucer == true 
      then rt = (saucer_radius - 0.5) + (0.5 * saucer_thickness)
      else rt = (saucer_radius + 0.5) - (0.5 * saucer_thickness)  
      end
    local start_thin_saucer = (saucer_sector_angle * j) - (max_value *0.5*saucer_sector_angle*thin_saucer_circ)
    local stop_thin_saucer = (saucer_sector_angle * j) + (max_value *0.5*saucer_sector_angle*thin_saucer_circ)
    if total_angle < 0 then
    cairo_arc_negative(display, x, y, rt, angle_to_position(cup_start_angle, start_thin_saucer), angle_to_position(cup_start_angle, stop_thin_saucer))
    else
    cairo_arc(display, x, y, rt, angle_to_position(cup_start_angle, start_thin_saucer), angle_to_position(cup_start_angle, stop_thin_saucer))
    end
    cairo_set_source_rgba(display, rgb_to_r_g_b(saucer_fg_clr, saucer_fg_alpha))
    cairo_set_line_width(display, 1)
    cairo_stroke(display)
   end
--saucer mark
    if saucer_mark_fg_alpha > 0 then 
    local start_cm = (saucer_sector_angle * value) - (handle_circ *0.5 )
    local stop_cm = (saucer_sector_angle * value) + (handle_circ *0.5 )
    if total_angle < 0 then
      cairo_arc_negative(display, x, y, saucer_radius, angle_to_position(cup_start_angle, start_cm), angle_to_position(cup_start_angle, stop_cm))
    else
      cairo_arc(display, x, y, saucer_radius, angle_to_position(cup_start_angle, start_cm), angle_to_position(cup_start_angle, stop_cm))
    end
    cairo_set_source_rgba(display, rgb_to_r_g_b(saucer_mark_fg_clr, saucer_mark_fg_alpha))
        cairo_set_line_width(display, saucer_thickness)
        cairo_stroke(display)
    end 
--graduation mark 
     if graduation_radius > 0 and graduation_thickness > 0 and graduation_mark_angle > 0 then
        number_graduation = (math.abs(total_angle) +1)/ graduation_mark_angle
        local start_arc_grad = 0
        local stop_arc_grad = 0
    local i = 0
        while i < number_graduation do            
            local start_arc_grad = (graduation_mark_angle * (i)) - (graduation_mark_circ *0.5)
            local stop_arc_grad = (graduation_mark_angle * (i)) + (graduation_mark_circ *0.5)
            if total_angle < 0 then
          cairo_arc_negative(display, x, y, graduation_radius, angle_to_position(cup_start_angle, start_arc_grad), angle_to_position(cup_start_angle, stop_arc_grad))
        else
          cairo_arc(display, x, y, graduation_radius, angle_to_position(cup_start_angle, start_arc_grad), angle_to_position(cup_start_angle, stop_arc_grad))
        end
        cairo_set_source_rgba(display,rgb_to_r_g_b(graduation_fg_clr,graduation_fg_alpha))
            cairo_set_line_width(display, graduation_thickness)
        cairo_stroke(display)            
            i = i + 1
        end
    end   
-- text
  if txt_fg_alpha>0 then 
    cairo_select_font_face (display, "hooge 05_53", CAIRO_FONT_SLANT_NORMAL, txt_weight);
    cairo_set_font_size (display,txt_size)
    cairo_set_source_rgba (display, rgb_to_r_g_b(txt_fg_clr, txt_fg_alpha))
    cairo_move_to (display,x+xtxt,y+ytxt)
    cairo_show_text (display, caption ) cairo_show_text (display,value)cairo_show_text (display, caption2 )
    cairo_stroke (display)
  end
end
-------------------------------------------------------------------------------
-- loads data and displays table_settings

function display_coffee_table(display)
    local function load_coffee_table(display, data)
        local str, value = '', 0       
    if data['name'] == 'time2' then
        local max_value = data['max_value']
            str = string.format('${time %s}', data['arg'])
            str = conky_parse(str)
            local value2 = tonumber(str:sub(0,2))
        if value2 == max_value then value2 = 0 end
        value = value2 + (tonumber(str:sub(4,5))/60)                
    else
            str = string.format('${%s %s}',data['name'], data['arg'])
            str = conky_parse(str)
            value = tonumber(str)
        end     
        if value == nil then value = 0 end
        draw_coffee_table(display, data, value)
    end
    for i in pairs(coffee_table) do
        load_coffee_table(display, coffee_table[i])
    end
end
-------------------------------------------------------------------------------
runscheck = 0 -- fix for draw shades running script twice on every update
function conky_main()
    if conky_window == nil then 
        return
    end
    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    local display = cairo_create(cs)
    local updates = conky_parse('${updates}')
    update_num = tonumber(updates)
    if update_num > 5 then
      cairo_set_antialias (display, CAIRO_ANTIALIAS_SUBPIXEL)
      display_coffee_table(display)
      cairo_set_antialias (display, CAIRO_ANTIALIAS_DEFAULT)
    end    
    cairo_surface_destroy(cs)
    cairo_destroy(display)
end

```chrono-full.template.lua

```

--[[
 The latest script is a lua only weather script. aka: v9000
 http://crunchbang.org/forums/viewtopic.php?id=16100

 the file:
 http://dl.dropbox.com/u/19008369/weatheragain9000.lua.tar.gz

 mrppeachys LUA Tutorial
 http://crunchbang.org/forums/viewtopic.php?id=17246
 edits by Jed
]]
_G.weather_script = function()--#### DO NOT EDIT THIS LINE ##############
--these tables hold the coordinates for each repeat do not edit #########
top_left_x_coordinate={}--###############################################
top_left_y_coordinate={}--###############################################
--#######################################################################
--SET DEFAULTS ##########################################################
--set defaults do not localise these defaults if you use a seperate display script
default_font="Arial"--font must be in quotes
default_font_size=14
default_color=0xffffff    --white
default_alpha=1        --fully opaque
default_image_width=50
default_image_height=50
-- ## New Options ###
default_face="bold"
-- "normal" for normal/normal
-- "bold" for normal/bold
-- "italic" for italic/normal
-- "bolditalic" for italic/bold
--END OF DEFAULTS #######################################################
--START OF WEATHER CODE -- START OF WEATHER CODE -- START OF WEATHER CODE

-- forecast
datay=375
datayy=15 --datay+(datayy*1)

datafx1=20

imgx=35
imgy=500
imgyy=60 -- imgy+(imgyy*1)
-- =============================================================================
-- Sun & Moon Rise -------------------------------------------------------------
   out({c=0xFAFAEC,a=1,x=10,y=35,txt="Sunrise"})
      out({c=0xFAFAEC,a=1,x=20,y=50,txt=sun_rise_time[1]})
   out({c=0xC0C0C0,a=1,x=382,y=40,txt="Moonrise"})
      out({c=0xC0C0C0,a=1,x=389,y=55,txt=moon_rise_time[1]})
-- Sun & Moon Set --------------------------------------------------------------
   out({c=0xFAFAEC,a=1,x=10,y=392,txt="Sunset"})
      out({c=0xFAFAEC,a=1,x=15,y=407,txt=sun_set_time[1]})
   out({c=0xC0C0C0,a=1,x=382,y=412,txt="Moonset"})
      out({c=0xC0C0C0,a=1,x=389,y=427,txt=moon_set_time[1]})
-- Moon Phase - Top Center Circle ----------------------------------------------
   out({c=0x227992,a=1,x=180,y=270,txt=moon_phase[1]})
   image({x=203,y=202,w=55,h=55,file=moon_icon[1]})
-- image({x=148,y=67,w=55,h=55,file="/media/5/Conky/images/red_1.png"})

-- Forecast for Today - see Day# Circle - Left ---------------------------------
   out({c=0xFF8C00,fs=14,a=1,x=280,y=160,txt=high_temp[1]})
   image({x=246,y=150,w=80,h=80,file=weather_icon[1]})
-- image({x=70,y=150,w=50,h=50,file="/media/5/Conky/images/red_1.png"})
   out({c=0x00BFFF,fs=14,a=1,x=280,y=230,txt=low_temp[1]})

-- Above the Month Circle on the Right -----------------------------------------
-- Humidity
   out({c=0xFAFAEC,a=1,x=285,y=120,txt="Hum:"})
      out({c=0x227992,a=1,x=323,y=120,txt=now["humidity"].."%"})
-- Chance of Rain
   out({c=0xFAFAEC,a=1,x=300,y=140,txt="Rain:"})
      out({c=0x227992,a=1,x=340,y=140,txt=precipitation[1].."%"})
-- Wind Info - See Months Circle & below ---------------------------------------
   image({x=310,y=205,w=75,h=75,file=now["wind_icon"]})
-- image({x=235,y=150,w=50,h=50,file="/media/5/Conky/images/red_1.png"})
   out({c=0x227992,a=1,x=285,y=295,txt=now["wind_mph"]})
-- out({c=0x48D1CC,a=1,x=240,y=260,txt=now["wind_nesw"]})
   out({c=0xFAFAEC,a=1,x=333,y=295,txt="@"})
      out({c=0x227992,a=1,x=355,y=295,txt=now["wind_deg"]})
-- Dew Point -------------------------------------------------------------------
   out({c=0xFAFAEC,a=1,x=145,y=355,txt="DP:"})
      out({c=0x227992,a=1,x=175,y=355,txt=now["dew_point"].."°"})

-- Above Day# Circle on left ---------------------------------------------------
-- Cloud Cover
   out({c=0xFAFAEC,a=1,x=320,y=160,txt="CC:"})
      out({c=0x227992,a=1,x=350,y=160,txt=cloud_cover[1].."%"})
-- Ceiling
   out({c=0xFAFAEC,a=1,x=330,y=180,txt="Ceil:"})
      out({c=0x227992,a=1,x=360,y=180,txt=now["ceiling"]})
-- Current for Today - Day# Circle ---------------------------------------------
   out({c=0xFAFAEC,a=1,x=215,y=300,txt="T:"})
      out({c=0xFF8C00,fs=14,a=1,x=230,y=300,txt=now["temp"].."°"})
   image({x=205,y=303,w=55,h=55,file=now["weather_icon"]})
-- image({x=132,y=218,w=85,h=85,file="/media/5/Conky/images/red_1.png"})
   out({c=0xFAFAEC,a=1,x=215,y=375,txt="F:"})
      out({c=0x00BFFF,fs=14,a=1,x=230,y=375,txt=now["feels_like"].."°"})
-- Below day# Circle on left ---------------------------------------------------
-- Barometric Pressure
out({c=0xFAFAEC,a=1,x=85,y=315,txt=" BP:"})
    out({c=0x227992,a=1,x=115,y=315,txt=now["pressure_mb"]})
-- UV
out({c=0xFAFAEC,a=1,x=115,y=335,txt="UV:"})
   out({c=0x227992,a=1,x=142,y=335,txt=uv_index_num[1]})
      out({c=0x227992,a=1,x=155,y=335,txt=uv_index_txt[1]})

-- Forecast for the next 3 hours -----------------------------------------------
-- image({x=5,y=353,w=340,h=2,file="/media/5/Conky/images/LightSlateGrey_1.png"})
out({c=0x227992,a=1,f="Arial",fs=16,x=33,y=448,txt="Next 3"})
out({c=0x227992,a=1,f="Arial",fs=16,x=35,y=463,txt="Hours"})
-- 1st hour
out({c=0xFF9600,x=98,y=470,txt=now["fc_hour1_time"]..":00"})
image({w=60,h=60,x=80,y=475,file=now["fc_hour1_wicon"]}) -- image({w=30,h=30,x=223,y=55,file="/home/sector11/Conky/images/red_1.png"})
out({c=0xAFAFAF,x=95,y=550,txt=now["fc_hour1_temp"] .."°"})
-- 2nd hour
out({c=0xFF9600,x=205,y=470,txt=now["fc_hour2_time"]..":00"})
image({w=60,h=60,x=190,y=475,file=now["fc_hour2_wicon"]}) -- image({w=30,h=30,x=223,y=130,file="/home/sector11/Conky/images/red_1.png"})
out({c=0xAFAFAF,x=205,y=550,txt=now["fc_hour2_temp"] .."°"})
-- 3rd hour
out({c=0xFF9600,x=317,y=470,txt=now["fc_hour3_time"]..":00"})
image({w=60,h=60,x=295,y=475,file=now["fc_hour3_wicon"]}) -- image({w=30,h=30,x=223,y=215,file="/home/sector11/Conky/images/red_1.png"})
out({c=0xAFAFAF,x=315,y=550,txt=now["fc_hour3_temp"] .."°"})

-- =============================================================================
-- FORECAST for the next 9 days
-- Forecast day 2 -- x = l|r  y = u|d

--########################################################################################
--END OF WEATHER CODE ----END OF WEATHER CODE ----END OF WEATHER CODE ---
--#######################################################################
end--of weather_display function do not edit this line ##################
--#######################################################################
```

---

### Post by Habitual on 2013-01-11
Thanks Jed!

---

### Post by Sector11 on 2013-01-11
I wasn't under 7 but I was under 8 minutes:

[[IMG]http://t.imgbox.com/acx9w6nK.jpg[/IMG]](http://imgbox.com/acx9w6nK) ... [[IMG]http://t.imgbox.com/abbcYCYz.jpg[/IMG]](http://imgbox.com/abbcYCYz)

---

### Post by Sector11 on 2013-01-11
> **Haghiri75 said:**
> &#1617;Is it Independent ? or Based on other distros?

VastOne created this originally using Debian NetInstall directly to Debian SID, hence the name V-SID-O, and a script to add XFCE4 and OpenBox sessions.  It was inspired by #! Statler that had OpenBox and XFCE4 sessions but the XFCE4 has since been dropped.  VSIDO uses the Debian Repos.

He has done some heavy customization with tint2 and gmusicbrowser.  [Here is what it is all about.]("http://vsido.freeforums.org/what-is-vsido-why-should-i-care-t18.html")

Another screen:

[[IMG]http://t.imgbox.com/aciW0oam.jpg[/IMG]](http://imgbox.com/aciW0oam)

---

### Post by flyffdzder on 2013-01-11
The post is very good.

---

### Post by Habitual on 2013-01-11
> **Jedcurtis said:**
> One thing to note;  If you don't have mrpeachy's v9000 weather script, the weather portion wont work.

I still use conkyforecast via [c-li script]("http://www.bournetoraiseshell.com/article.php/20101101123337204").
It's only a four day forecast, but I like it b/c I wrote it.
Just like conky's {goto } statements, but using tput.

Hey Sector11, they let anyone in here?):P

---

### Post by SpaceAviator on 2013-01-12
In the end it all comes down to personal preference but after that aesthetically pleasing login screen, the default xfce desktop was just so...glossy. Gloss. Gloss everywhere.

---

### Post by Sector11 on 2013-01-12
> **SpaceAviator said:**
> In the end it all comes down to personal preference but after that aesthetically pleasing login screen, the default xfce desktop was just so...glossy. Gloss. Gloss everywhere.

Just like the Military, if you can't see your face in it, buff it up more!

Or since this isn't a "YES SIR! NO SIR! Three bags full SIR!" situation:

[LIST][*]change the theme[/LIST]
Greatest thing about Linux - *it comes complete with options!*

---

### Post by SpaceAviator on 2013-01-12
> **Sector11 said:**
> Just like the Military, if you can't see your face in it, buff it up more!

Or since this isn't a "YES SIR! NO SIR! Three bags full SIR!" situation:

[LIST][*]change the theme[/LIST]
Greatest thing about Linux - *it comes complete with options!*

Thus my personal preference comment :P

---

### Post by Sector11 on 2013-01-12
> **Habitual said:**
> I still use conkyforecast via [c-li script]("http://www.bournetoraiseshell.com/article.php/20101101123337204").
It's only a four day forecast, but I like it b/c I wrote it.
Just like conky's {goto } statements, but using tput.

Hey Sector11, they let anyone in here?):P

And you though you had exclusive rights!  \\:D/ :lolflag:

I must try that script. Anything special I need to know?

I still use the regular conkyForecast, see below, one conky, 4 cities

---

### Post by Sector11 on 2013-01-12
> **SpaceAviator said:**
> Thus my personal preference comment :P

:D  Gotta LOVE Linux ... BTW, how close did you het to the 7 minute mark?  Mine was 8 min something.

---

### Post by Sector11 on 2013-01-12
> **Habitual said:**
> I still use conkyforecast via [c-li script]("http://www.bournetoraiseshell.com/article.php/20101101123337204").

Thank you, that's really slick!
I had to make changes, ie:
```
echo "Low: " `/usr/bin/conkyForecast.py --location=USOH1096 -d LT --imperial --startday 1`
```
became:
```
echo "Low: " `conkyForecast --location=ARBA0009 -d LT --startday 1`
```

```
 sector11 @ sector11
 12 Jan 13 | 13:48:39 ~
         $ 4days
Forecast for Sun, Jan 13 2013           Forecast for Mon, Jan 14 2013
----------------------------            ----------------------------
Low:  22°C                              Low:  22°C
High: 33°C                              High: 32°C
Humidity: 44%                           Humidity: 48%
Clear                                   Clear
Precipitation: 0%                       Precipitation: 0%


Forecast for Tue, Jan 15 2013           Forecast for Wed, Jan 16 2013
----------------------------            ----------------------------
Low:  23°C                              Low:  22°C
High: 32°C                              High: 32°C
Humidity: 51%                           Humidiy: 55%
Fair                                    Scattered Thunderstorms
Precipitation: 0%                       Precipitation: 60%

 sector11 @ sector11
 12 Jan 13 | 13:48:43 ~
         $
```
[COLOR="Teal"]**EXCELLENT!!!!  Well done!**[/COLOR]
Now I gotta play with it, I see 2 more days in there easy.  ):P

---

### Post by Habitual on 2013-01-12
> **Sector11 said:**
> ...Anything special I need to know?...

I use 
--imperial ? ;)

---

### Post by Sector11 on 2013-01-12
> **Habitual said:**
> I use 
--imperial ? ;)

Yea I caught that, I was playing for a bit, had other things to do and just got back.  I hard coded the longest "conditions text" in there just to check spacing.  I think I'm going to get a full 10 days in there.  :D

Again, thank you!
```
 Sun, 13 Jan 2013                        Mon, Jan 14 2013
----------------------------------      ----------------------------------
H: 33°C  L: 22°C                        L  22°C   H:  32°C
Hum 44%
                                        Hum 45%
Clear                                   Clear
CoR  0%                                 CoR  0%


 Tue, Jan 15                             Wed, Jan 16 2013
----------------------------------      ----------------------------------
L  23°C                                 L  22°C
H:  32°C                                H:  32°C
Hum 51%                                 Hum 55%
Fair                                    Scattered Thunderstorms
CoR  0%                                 CoR  60%




----------------------------------
Chance of Scattered Thunderstorms
 sector11 @ sector11
 12 Jan 13 | 19:30:40 ~
         $ 
```

CoR (Chance of Rain) will go beside Hum

---

### Post by Sector11 on 2013-01-13
> **Habitual said:**
> I use 
--imperial ? ;)

Check it out ... a full week!
[[IMG]http://t.imgbox.com/adfFAKzc.jpg[/IMG]](http://imgbox.com/adfFAKzc)

```
#!/bin/bash
# --- original ---
# 4 Day Weather forecast script for Boardman, OH
# Written by John Jones ie: Habitual
# 11.01.2010 12:10:07
# --- Edited by Sector11 ---
# 7 Day Forecast
# ~/bin/cf7
# 13 Jan 2013 14:08 UTC
# conkyForecast by: Kaivalagi


# Clear the screen
tput clear
# Today (Left 1st Group)
tput cup 0 0
echo "Today" `date --date="0 day" | awk '{print $1", "$3" "$2" "$6}'`
tput cup 1 0
echo "----------------------------------"
tput cup 2 0
tput bold; tput setaf 2;
echo "C" `conkyForecast --location=ARBA0009 -d HT --hideunits`
tput cup 2 8
tput bold; tput setaf 6;
echo "±" `conkyForecast --location=ARBA0009 -d LT --hideunits`
tput sgr0
tput cup 2 16
echo "Hum" `conkyForecast --location=ARBA0009 -d HM  --startday 0`
tput cup 2 25
echo "CoR" `conkyForecast --location=ARBA0009 -d PC --startday 0`
tput cup 3 0
echo `conkyForecast --location=ARBA0009 -d CT --startday 0`


# Today Forcast (Right 1st Group)
tput cup 0 40
echo "Today Continues"
tput cup 1 40
echo "----------------------------------"
tput cup 2 40
tput bold; tput setaf 2;
echo "H" `conkyForecast --location=ARBA0009 -d HT --hideunits --startday 0`
tput cup 2 48
tput bold; tput setaf 6;
echo "L" `conkyForecast --location=ARBA0009 -d LT --hideunits --startday 0`
tput sgr0
tput cup 2 56
echo "SR" `conkyForecast --location=ARBA0009 -d SR  --startday 0`
tput cup 2 65
echo "SS" `conkyForecast --location=ARBA0009 -d SS --startday 0`
tput cup 3 40
tput bold; tput setaf 2;
echo "Bar" `conkyForecast --location=ARBA0009 -d BR`
tput cup 3 53
tput bold; tput setaf 6;
echo `conkyForecast --location=ARBA0009 -d BD`
tput sgr0
tput cup 3 64
echo "Day" `conkyForecast --location=ARBA0009 -d DL --startday 0`


# Tomorrow (Left - 2nd Group)
tput cup 5 0
echo `date --date="1 day" | awk '{print $1", "$3" "$2" "$6}'`
tput cup 6 0
echo "----------------------------------"
tput cup 7 0
tput bold; tput setaf 2;
echo "H" `conkyForecast --location=ARBA0009 -d HT --hideunits --startday 1`
tput cup 7 8
tput bold; tput setaf 6;
echo "L" `conkyForecast --location=ARBA0009 -d LT --hideunits --startday 1`
tput sgr0
tput cup 7 16
echo "Hum" `conkyForecast --location=ARBA0009 -d HM  --startday 1`
tput cup 7 25
echo "CoR" `conkyForecast --location=ARBA0009 -d PC --startday 1`
tput cup 8 0
echo `conkyForecast --location=ARBA0009 -d CT --startday 1`
tput sgr0

# Tomorrow +1...(Right - 2nd Group)
tput cup 5 40
echo `date --date="2 day" | awk '{print $1", "$3" "$2" "$6}'`
tput cup 6 40
echo "----------------------------------"
tput cup 7 40
tput bold; tput setaf 2;
echo "H" `conkyForecast --location=ARBA0009 -d HT --hideunits --startday 2`
tput cup 7 48
tput bold; tput setaf 6;
echo "L" `conkyForecast --location=ARBA0009 -d LT --hideunits --startday 2`
tput sgr0
tput cup 7 56
echo "Hum" `conkyForecast --location=ARBA0009 -d HM  --startday 2`
tput cup 7 65
echo "CoR" `conkyForecast --location=ARBA0009 -d PC --startday 2`
tput cup 8 40
echo `conkyForecast --location=ARBA0009 -d CT --startday 2`
tput sgr0

# Tomorrow +2...(Left 3rd Group)
tput cup 10 0
echo `date --date="3 day" | awk '{print $1", "$3" "$2" "$6}'`
tput cup 11 0
echo "----------------------------------"
tput cup 12 0
tput bold; tput setaf 2;
echo "H" `conkyForecast --location=ARBA0009 -d HT --hideunits --startday 3`
tput cup 12 8
tput bold; tput setaf 6;
echo "L" `conkyForecast --location=ARBA0009 -d LT --hideunits --startday 3`
tput sgr0
tput cup 12 16
echo "Hum" `conkyForecast --location=ARBA0009 -d HM  --startday 3`
tput cup 12 25
echo "CoR " `conkyForecast --location=ARBA0009 -d PC --startday 3`
tput cup 13 0
echo `conkyForecast --location=ARBA0009 -d CT --startday 3`

# Tomorrow +3...(Right 3rd Group)
tput cup 10 40
echo `date --date="4 day" | awk '{print $1", "$3" "$2" "$6}'`
tput cup 11 40
echo "----------------------------------"
tput cup 12 40
tput bold; tput setaf 2;
echo "H" `conkyForecast --location=ARBA0009 -d HT --hideunits --startday 4`
tput cup 12 48
tput bold; tput setaf 6;
echo "L" `conkyForecast --location=ARBA0009 -d LT --hideunits --startday 4`
tput sgr0
tput cup 12 56
echo "Hum" `conkyForecast --location=ARBA0009 -d HM  --startday 4`
tput cup 12 65
echo "CoR" `conkyForecast --location=ARBA0009 -d PC --startday 4`
tput cup 13 40
echo `conkyForecast --location=ARBA0009 -d CT --startday 4`

# Tomorrow +4...(Left 4th Group)
tput cup 15 0
echo `date --date="5 day" | awk '{print $1", "$3" "$2" "$6}'`
tput cup 16 0
echo "----------------------------------"
tput cup 17 0
tput bold; tput setaf 2;
echo "H" `conkyForecast --location=ARBA0009 -d HT --hideunits --startday 5`
tput cup 17 8
tput bold; tput setaf 6;
echo "L" `conkyForecast --location=ARBA0009 -d LT --hideunits --startday 5`
tput sgr0
tput cup 17 16
echo "Hum" `conkyForecast --location=ARBA0009 -d HM  --startday 5`
tput cup 17 25
echo "CoR " `conkyForecast --location=ARBA0009 -d PC --startday 5`
tput cup 18 0
echo `conkyForecast --location=ARBA0009 -d CT --startday 5`

# Tomorrow +5...(Right 4th Group)
tput cup 15 40
echo `date --date="6 day" | awk '{print $1", "$3" "$2" "$6}'`
tput cup 16 40
echo "----------------------------------"
tput cup 17 40
tput bold; tput setaf 2;
echo "H" `conkyForecast --location=ARBA0009 -d HT --hideunits --startday 6`
tput cup 17 48
tput bold; tput setaf 6;
echo "L" `conkyForecast --location=ARBA0009 -d LT --hideunits --startday 6`
tput sgr0
tput cup 17 56
echo "Hum" `conkyForecast --location=ARBA0009 -d HM  --startday 6`
tput cup 17 65
echo "CoR" `conkyForecast --location=ARBA0009 -d PC --startday 6`
tput cup 18 40
echo `conkyForecast --location=ARBA0009 -d CT --startday 6`

tput sgr0
tput cup 22 0
```

---

### Post by KosakiHook on 2013-01-14
Very nice.

Puppy Linux is also a quick install.  I can do a frugal install in 5 minutes or less.

---

### Post by Habitual on 2013-01-14
> **Jedcurtis said:**
> VastOne, amazing as always!  VSIDO is totally awesome.  Here is a scrot of the install completing in less than 7 minutes!  [[IMG]http://www.zimagez.com/miniature/screenshot-01112013-010730pm.png[/IMG]]("http://www.zimagez.com/zimage/screenshot-01112013-010730pm.php")

back on Topic...

Looks good ;)

---

### Post by Jedcurtis on 2013-01-16
> **Habitual said:**
> back on Topic...

Looks good ;)
Now one of the testers has one in less than 5 minutes!  This Distro is absolutely amazing!!!

---

### Post by sffvba[e0rt on 2013-01-16
Hmmm, this distro has prickled my curiosity (which hasn't happened in a while), I guess it is time to fire it up in VBox and see what it is all about.


404

---

### Post by Jedcurtis on 2013-01-16
> **not found said:**
> Hmmm, this distro has prickled my curiosity (which hasn't happened in a while), I guess it is time to fire it up in VBox and see what it is all about.


404
After all the Distro hopping over the years, this is the one for me!  Doesn't crash, runs quick, light on resources and just an all around great debian based Distro.  And of course, we all know debian is the best there is... :D

---

### Post by offgridguy on 2013-01-16
> **Jedcurtis said:**
> After all the Distro hopping over the years, this is the one for me!  Doesn't crash, runs quick, light on resources and just an all around great debian based Distro.  And of course, we all know debian is the best there is... :D
How does it rate against lubuntu ?

---

### Post by SpaceAviator on 2013-01-17
> **Jedcurtis said:**
> Now one of the testers has one in less than 5 minutes!  This Distro is absolutely amazing!!!

You sound like you are on the VSIDO's PR team :lol:

---

### Post by Jedcurtis on 2013-01-17
> **offgridguy said:**
> How does it rate against lubuntu ?

First off, I have nothing against any of the Ubuntu flavors!  That said, VSIDO is faster, leaner, and easier to make 'your own'!  This is just "my opinion", and in no way meant to belittle Ubuntu!  I've had a lot of fun with many different releases of Ubu in it's various forms and versions!

Jed

---

### Post by Jedcurtis on 2013-01-17
> **SpaceAviator said:**
> You sound like you are on the VSIDO's PR team :lol:

Actually that's a good idea!!!  VSIDO needs a PR team!  Everyone should be made aware of it IMO.  I'm just really happy after a lot of years jumping from Distro to Distro....

---

### Post by VastOne on 2013-01-17
@ SpaceAviator..  :p

Thanks @Jedcurtis!

---

### Post by offgridguy on 2013-01-17
Any place to buy a live CD?  My internet connection is not good for downloads.

---

### Post by snowpine on 2013-01-17
> **offgridguy said:**
> Any place to buy a live CD?  My internet connection is not good for downloads.

Don't used a Sid-based distro if you have a slow connection; it will receive many megabytes of upgrades each week!

---

### Post by offgridguy on 2013-01-17
> **snowpine said:**
> Don't used a Sid-based distro if you have a slow connection; it will receive many megabytes of upgrades each week!
Thanks, i have learned from Sabayon that a rolling release isn't for me.  This is the first i have heard of Sid-based, could you expand on it a bit for me, please.

---

### Post by snowpine on 2013-01-17
> **offgridguy said:**
> Thanks, i have learned from Sabayon that a rolling release isn't for me.  This is the first i have heard of Sid-based, could you expand on it a bit for me, please.

Sid is the "unstable" branch of Debian, which means it is constantly changing. 

[http://www.debian.org/releases/sid/](http://www.debian.org/releases/sid/)

> The code name for Debian's development distribution is "sid", aliased to "unstable". Most of the development work that is done in Debian, is uploaded to this distribution. This distribution will never get released; instead, packages from it will propagate into testing and then into a real release.

Please note that security updates for "unstable" distribution are not managed by the security team. Hence, "unstable" does not get security updates in a timely manner. For more information please see the Security Team's FAQ.

"sid" is subject to massive changes and in-place library updates. This can result in a very "unstable" system which contains packages that cannot be installed due to missing libraries, dependencies that cannot be fulfilled etc. Use it at your own risk!

It is not "rolling release" because it is not a "release." It is just "rolling."

---

### Post by offgridguy on 2013-01-17
Thank you for the explanation, snowpine :D.

---

### Post by Sector11 on 2013-01-17
> **snowpine said:**
> it is not "rolling release" because it is not a "release." it is just "rolling."

priceless! :KS :KS :KS :KS :KS

---

### Post by Sector11 on 2013-01-17
> **offgridguy said:**
> Thank you for the explanation, snowpine :D.

Edmonchuck?

---

### Post by Jedcurtis on 2013-01-18
> **offgridguy said:**
> Thanks, i have learned from Sabayon that a rolling release isn't for me.  This is the first i have heard of Sid-based, could you expand on it a bit for me, please.

First, yes it is considered a 'Rolling Release'  This means the latest versions of everything under the sun!  Newer versions of Gimp for example than what is currently available in the Ubuntu repositories.  This does NOT mean that it is 'unstable'; that is a misnomer.
As to the many megabytes of downloads, it is like anything else with Linux, you are free to download them or not.  If your happy with what you have then just don't download a particular package.
Since using VSIDO, I have not experienced one crash or lockup!  I'm definitely not a Linux guru either by any definition of the word!
In other words, if I can get it running on my laptop, I would think anyone could get it installed and running.  IMO it is easier and faster to install than Ubuntu, and much easier on your systems resources!
The official release was today, and the article to announce that can be found at this link;
[http://www.jedsdesk.com/?p=838](http://www.jedsdesk.com/?p=838)

Hope this clears things up a little bit!!!!

Jed

---

### Post by sffvba[e0rt on 2013-01-18
Well all the best with the distro.  I installed in VBox, not sure what I was expecting, but this isn't what I am looking for in a distro anymore.


404

---

### Post by Jedcurtis on 2013-01-21
Not sure if I mentioned the [VSIDO Community forums]("http://vsido.org/index.php").  We have some of the greatest Conky minds assembled at our Conky thread, that I'd be remiss by not pointing you to it!  It is found [here]("http://vsido.org/index.php/board,5.0.html")...
Come make yourself at home.  You don't have to be using VSIDO to check out our Conky contribs...
Jed :)

---

