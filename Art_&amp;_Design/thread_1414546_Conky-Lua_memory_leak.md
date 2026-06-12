---
title: "Conky-Lua memory leak"
date: 2010-02-23
forum: Art &amp; Design
---

### Post by jacobmh on 2010-02-23
I recently began using one of londonali's LUA scripts for drawing a shaded background to a conky window. Unfortunately, it seems to have a **huge** memory leak (the leak grows at a rate of 10 mb an hour) no matter what conkyrc file I call it with. 

Does anyone have a fix? Here is the LUA script:

```
--[[
Background by londonali1010 (2009)

This script draws a background to the Conky window. It covers the whole of the Conky window, but you can specify rounded corners, if you wish.

To call this script in Conky, use (assuming you have saved this script to ~/scripts/):
	lua_load ~/scripts/draw_bg.lua
	lua_draw_hook_pre draw_bg

Changelog:
+ v1.0 -- Original release (07.10.2009)
]]

-- Change these settings to affect your background.
-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.

corner_r=15

-- Set the colour and transparency (alpha) of your background.

bg_colour=0x00000
bg_alpha=0.5

require 'cairo'
function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function conky_draw_bg()
	if conky_window==nil then return end
	local w=conky_window.width
	local h=conky_window.height
	local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
	cr=cairo_create(cs)
	
	cairo_move_to(cr,corner_r,0)
	cairo_line_to(cr,w-corner_r,0)
	cairo_curve_to(cr,w,0,w,0,w,corner_r)
	cairo_line_to(cr,w,h-corner_r)
	cairo_curve_to(cr,w,h,w,h,w-corner_r,h)
	cairo_line_to(cr,corner_r,h)
	cairo_curve_to(cr,0,h,0,h,0,h-corner_r)
	cairo_line_to(cr,0,corner_r)
	cairo_curve_to(cr,0,0,0,0,corner_r,0)
	cairo_close_path(cr)
	
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
	cairo_fill(cr)
end
```

My theory is that whenever my conkyrc updates itself (I mainly use it for system stats, time, and some rss feeds), it redraws the window and leaves crap behind. Any thoughts?

---

### Post by jacobmh on 2010-02-23
buuump.

---

### Post by jacobmh on 2010-02-24
I guess no one here can figure it out, then.

---

### Post by londonali1010 on 2010-02-26
Hi jacobmh,

You could always PM me! :)

This was an older script and I haven't really kept it up to date.  Try adding in
```
cairo_destroy(cr)
```
just above the last "end"...Does that fix it?  It should destroy the drawing surface after each iteration and release the memory (I think).

I'm sort of a "needs, must" programmer, so it's entirely possible for this stuff to come up.  Thanks for using the script, and posting the problem!

---

### Post by fallofahero on 2011-02-27
i have same problem but doesn't work for me 

my lua : 

```
settings_table = {
    {
        name='fs_used_perc',
        arg='/home',
        max=100,
        bg_colour=0xffffff,
        bg_alpha=0,
        fg_colour=0xff0000,
        fg_alpha=0.1,
        x=178, y=690,
        radius=33,
        thickness=35,
        angle=91
    },
    {

        name='cpu',
        arg='cpu0',
        max=100,
        bg_colour=0x000000,
        bg_alpha=0.12,
        fg_colour=0xffffff,
        fg_alpha=0.2,
        x=78, y=359,
        radius=20,
        thickness=10,
        angle=270
    },
    {
        name='cpu',
        arg='cpu1',
        max=100,
        bg_colour=0x000000,
        bg_alpha=0.12,
        fg_colour=0xffffff,
        fg_alpha=0.2,
        x=152, y=359,
        radius=20,
        thickness=10,
        angle=90
    },
}

require 'cairo'

function rgb_to_r_g_b(colour,alpha)
    return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function draw_ring(t, pt)
    if conky_window==nil then return end
    local w,h=conky_window.width,conky_window.height
    local cs=cairo_xlib_surface_create(conky_window.display,conky_window.drawable,conky_window.visual,w,h)
    
    cr=cairo_create(cs)
    
    local xc,yc,ring_r,ring_w,angle=pt['x'],pt['y'],pt['radius'],pt['thickness'],pt['angle']
    local bgc, bga, fgc, fga=pt['bg_colour'], pt['bg_alpha'], pt['fg_colour'], pt['fg_alpha']

    local angle_0=angle*(2*math.pi/360)-math.pi/2
    local t_arc=t*2*math.pi

    -- Draw background ring

    cairo_arc(cr,xc,yc,ring_r,0,2*math.pi)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(bgc,bga))
    cairo_set_line_width(cr,ring_w)
    cairo_stroke(cr)
    
    -- Draw indicator ring

    cairo_arc(cr,xc,yc,ring_r,angle_0,angle_0+t_arc)
    cairo_set_source_rgba(cr,rgb_to_r_g_b(fgc,fga))
    cairo_stroke(cr)        
    
    cairo_destroy(cr)
    cr = nil
end

function conky_cairo_cleanup()
    cairo_surface_destroy(cs)
    cs = nil
end

function conky_ring_stats()
    local function setup_rings(pt)
        local str=''
        local value=0
        
        str=string.format('${%s %s}',pt['name'],pt['arg'])
        str=conky_parse(str)
        
        value=tonumber(str)
        pct=value/pt['max']
        
        draw_ring(pct,pt)
    end
    
    local updates=conky_parse('${updates}')
    update_num=tonumber(updates)
    
    if update_num>5 then
        for i in pairs(settings_table) do
            setup_rings(settings_table[i])
        end
    end

-- i add this
    cairo_destroy(cr) 

end
```

---

### Post by VinDSL on 2011-03-27
> **jacobmh said:**
> Does anyone have a fix?

> **jacobmh said:**
> buuump.

> **jacobmh said:**
> I guess no one here can figure it out, then.


Here you go...

Just took a year for someone to figure it out!  :D


```

--[[	Background by londonali1010 (2009)
	VinDSL Background Hack (2010-2011)

This script draws a background to the Conky window. It covers the whole of the Conky window, but you can specify rounded corners, if you wish.

To call this script in Conky, use (assuming you have saved this script to ~/scripts/):
	lua_load ~/scripts/draw_bg.lua
	lua_draw_hook_pre draw_bg

Changelog:
	+ v3.0	VinDSL Hack (01.28.2011) Killed memory leak.
	+ v2.4	VinDSL Hack (01.25.2011) Declared all variables in local.
	+ v2.3	VinDSL Hack (12.31.2010) Added shading example(s).
	+ v2.2	VinDSL Hack (12.30.2010) Cleaned up the code a bit.
	+ v2.1	VinDSL Hack (12.24.2010) Added cairo destroy function(s).
	+ v2.0	VinDSL Hack (12.21.2010) Added height adjustment variable.
	+ v1.0	Original release (07.10.2009)

]]

--------------START OF PARAMETERS ------------
-- Change these settings to affect your background:

-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.

	local corner_r = 50

-- Set the colour and transparency (alpha) of your background (0.00 - 0.99).

--	(Light Shading Example)
--	local bg_colour = 0x4d4d4d
--	local bg_alpha = 0.50

--	(Medium Shading Example)
--	local bg_colour = 0x222222
--	local bg_alpha = 0.50

--	(Dark Shading Example)
--	local bg_colour = 0x000000
--	local bg_alpha = 0.50

	local bg_colour = 0x000000
	local bg_alpha = 0.38

-- Tweaks the height of your background, in pixels. If you don't need to adjust the height, use 0.

--	(Default Setting)
--	local vindsl_hack_height = 0

	local vindsl_hack_height = -269
---------------END OF PARAMETERS -------------

require 'cairo'
local	cs, cr = nil

local function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
	end

function conky_draw_bg()
	if conky_window == nil then return end
	if cs == nil then cairo_surface_destroy(cs) end
	if cr == nil then cairo_destroy(cr) end
	local w = conky_window.width
	local h = conky_window.height
	local v = vindsl_hack_height
	local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
	local cr = cairo_create(cs)
	
	cairo_move_to(cr,corner_r,0)
	cairo_line_to(cr,w-corner_r,0)
	cairo_curve_to(cr,w,0,w,0,w,corner_r)
	cairo_line_to(cr,w,h+v-corner_r)
	cairo_curve_to(cr,w,h+v,w,h+v,w-corner_r,h+v)
	cairo_line_to(cr,corner_r,h+v)
	cairo_curve_to(cr,0,h+v,0,h+v,0,h+v-corner_r)
	cairo_line_to(cr,0,corner_r)
	cairo_curve_to(cr,0,0,0,0,corner_r,0)
	cairo_close_path(cr)

	cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
	cairo_fill(cr)

	cairo_surface_destroy(cs)
	cairo_destroy(cr)
	end


```

---

### Post by Doume on 2012-06-02
Hello to all
I've just installed Conky 1.9.0 on my Ubuntu 12.04 , hoping to solve the memory leak problem with version 1.8.1.
1.9.0 : Configure / compile / install OK !
But it's still the same : The memory leak problem is still alive....

---

