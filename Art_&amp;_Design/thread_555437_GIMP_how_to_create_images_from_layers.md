---
title: "GIMP how to create images from layers?"
date: 2007-09-20
forum: Art &amp; Design
---

### Post by digitalis_vulgaris on 2007-09-20
How to save all layers for gimp as separate images ?

---

### Post by amixroed on 2007-09-20
why don't you just copy each one and save them in a new image?

---

### Post by digitalis_vulgaris on 2007-09-20
I usually use around 30 layers...

---

### Post by SreckoMicic on 2007-09-20
One way is to show only layer you need, and then save it as png (or whatever you need). 
Don't know is there any plugin, or some kind of script to automatize that proces.

---

### Post by digitalis_vulgaris on 2007-09-20
Maybe it could be done with GIMP GAP ?

---

### Post by digitalis_vulgaris on 2007-09-21
I found same script-fu, and I believe this is staff I need, but I don't know how to insert it in GIMP and start it. Help ?! :(

=============================
;; sequence-file.scm -*-scheme-*-
;; Load Sequence (script-fu-sequence-load) - Load numbered sequence of images 
;;   from disk and  possibly combine them into one image
;;
;; Save Sequence (script-fu-sequence-save) - Save all layers to numbered 
;;   sequence of images on disk
;;
;; This is a version compatible with GIMP v1.1.22
;;
;; Copyright (C) 2000 by Jaroslav Benkovsky <edheldil@atlas.cz>
;; Released under General Public License (GPL)
;; 
;; $Id: sequence-file.scm,v 1.7 2000/07/02 22:26:16 benkovsk Exp $
;;
;; Requires:
;;   script-fu
;;
;; Notes:
;;   - loaded images should have one layer only, the rest is ignored
;;   - if any source image or layer doesn't exist, script aborts. Should be 
;;     changed?
;;
;; TODO:
;;   sequence-split --  split loaded image into one image for each layer
;;   sequence-merge -- merge loaded images into one image
;;   iterate -- apply user defined SIOD to each Image/Layer matching regexp
;;   specify image format

;; Example:
;;   (script-fu-sequence-load "worx/atomix/pov/m_intro%%.tga" "Layer % (replace)" 1 10 TRUE)
;;

;; split template into list

(define (string-template-split str first_number)
    (let* (
	   (tplchar "%")
	   (digits "0123456789")

	   (len (string-length str))
	   (f1 (strcspn str tplchar))
	   )

      (if (= f1 len)
	  (begin
	      (set! f1 (strcspn str digits))
	      (if (= f1 len) 
		  (error "Can't insert number to template" str)
		  (set! fs digits)))
	  (set! fs tplchar))

      (set! hdr (substring str 0 f1))
      (set! str (substring str f1 len))
      (set! len (- len f1))

      (set! f2 (strspn str fs))
      (set! body (substring str 0 f2))
      (set! ftr (substring str f2 len))

      (set! fill (string-length body))
      (if (eq? fs tplchar)
	  (set! body 0)
	  (set! body (- (string->number body 10) first_number)))

      (set! return (list hdr body ftr fill))
))

;; build string from template & param

(define (string-template-expand seq tpl)
    (begin
      (set! body (number->string (+ seq (cadr tpl)) 
			    10
			    (car (last tpl))))
      (set! str (string-append (car tpl) 
			       body 
			       (caddr tpl)))
))

;; Load Sequence

(define (script-fu-sequence-load filetpl layertpl 
				 first_frame last_frame 
				 make_one_image?)
    (let* (
	   (f_tpl (string-template-split filetpl first_frame))
	   (l_tpl (if (= make_one_image? TRUE)
			  (string-template-split layertpl first_frame)))
	   )

      (set! seq first_frame)
      (while (or (<= seq last_frame) (= last_frame 0))
	     (set! f_name (string-template-expand seq f_tpl))

	     (set! errobj ())
	     (set! qqq (gimp-file-load 1 f_name filetpl))
;	     (set! src_img (car (gimp-file-load 1 f_name filetpl)))

	     (if (eq? errobj ())     ; check for error during load
		 (begin
		   (set! src_img (car qqq))
		   (if (= make_one_image? TRUE)
		       (begin      ; (= make_one_image TRUE)
			 (set! l_name (string-template-expand seq l_tpl))
			 (set! layers (gimp-image-get-layers src_img))
			 ; (set! layer_cnt (car layers))
			 (set! src_layer (aref (cadr layers) 0))
			 (set! type (car (gimp-drawable-type src_layer)))

			 ;;(eval (read-from-string "(file-jpg-load ...)"))

			 (if (= seq first_frame)
			     (begin       ; (= seq first_frame)
			       (set! main_img src_img)
			       (set! width (car (gimp-drawable-width src_layer)))
			       (set! height (car (gimp-drawable-height src_layer)))
			       (gimp-image-undo-disable main_img))
			     (begin       ; (!= seq first_frame)
			       (gimp-edit-copy src_layer)
			       (set! tgt_layer (car (gimp-layer-new main_img width height type l_name 100 NORMAL)))
			       (gimp-image-add-layer main_img tgt_layer -1)
			       (gimp-edit-clear tgt_layer)
			       ; (set! tgt_layer (car (gimp-edit-paste tgt_layer 0)))
			       ; (gimp-floating-sel-anchor tgt_layer)
			       
			       (let ((floating-sel (car (gimp-edit-paste tgt_layer FALSE))))
				 (gimp-floating-sel-anchor floating-sel))
			       

			       (gimp-image-delete src_img))))
		       (begin      ; (!= make_one_image TRUE)
			 (gimp-image-clean-all src_img)
			 (gimp-display-new src_img)))
	     
		   (set! seq (+ seq 1)))
		 (begin  ; Error during load: (!= errobj ())
		   (error "eee" errobj)
		   (set! last_frame -1)))
	   )

      ; cleanup
      (if (= make_one_image? TRUE)
	  (begin 
	      (gimp-image-clean-all main_img)
	      (gimp-image-undo-enable main_img)
	      (gimp-display-new main_img)))
))

;; Save Sequence

(define (script-fu-sequence-save src_img drawable filetpl
				 first_frame last_frame 
				 preserve_size? preserve_bg?)

    (let* ((f_tpl (string-template-split filetpl first_frame))
	   (type (car (gimp-drawable-type drawable)))
	   (img_width (car (gimp-image-width src_img)))
	   (img_height (car (gimp-image-height src_img)))
	   (img_type (cond ((= type RGB_IMAGE) RGB)
			   ((= type RGBA_IMAGE) RGB)
			   ((= type GRAY_IMAGE) GRAY)
			   ((= type GRAYA_IMAGE) GRAY)
			   ((= type INDEXED_IMAGE) INDEXED)
			   ((= type INDEXEDA_IMAGE) INDEXED))))


      (set! layers (gimp-image-get-layers src_img))
      (set! layer_cnt (car layers))

      (if (or (> last_frame layer_cnt) (= last_frame 0))
	  (set! last_frame layer_cnt))

      ; FIXME: more checks for first_frame; but tpl's are already set!

      (set! seq first_frame)
      (while (<= seq last_frame)
	     (set! src_layer (aref (cadr layers) (- layer_cnt seq)))

	     (set! f_name (string-template-expand seq f_tpl))

	     (set! width (car (gimp-drawable-width src_layer)))
	     (set! height (car (gimp-drawable-height src_layer)))
	     (set! type (car (gimp-drawable-type src_layer)))


	     (gimp-edit-copy src_layer)

	     (set! tgt_img (car (gimp-image-new width height img_type)))
	     (set! tgt_layer (car (gimp-layer-new tgt_img width height type "layer" 100 NORMAL)))
	     (gimp-image-add-layer tgt_img tgt_layer 0)

	     (if (= preserve_bg? TRUE)
		 (begin
		   (gimp-edit-clear tgt_layer))
		 (begin
		   (gimp-drawable-fill tgt_layer BG-IMAGE-FILL)))

	     (let ((floating-sel (car (gimp-edit-paste tgt_layer FALSE))))
	       (gimp-floating-sel-anchor floating-sel))

	     (if (= preserve_size? TRUE)
		 (begin
		   (set! offset (gimp-drawable-offsets src_layer))
		   (gimp-image-resize tgt_img img_width img_height (car offset) (cadr offset))))

             (gimp-file-save 1 tgt_img tgt_layer f_name f_name)
	     (gimp-image-clean-all tgt_img)
	     (gimp-image-delete tgt_img)
	     (set! seq (+ seq 1))
	     )

))


(script-fu-register "script-fu-sequence-load"
		    "<Toolbox>/Xtns/Script-Fu/Utils/Load Sequence"
		    "Load numbered sequence of images from disk, possibly combining them into single image."
		    "Jaroslav Benkovsky <edheldil@atlas.cz>"
		    "Jaroslav Benkovsky"
		    "July 2000"
		    ""

		    SF-FILENAME   "File Name Template"  "pict%%.tga"
		    SF-STRING     "Layer Name Template" "Layer % (replace)"
		    SF-ADJUSTMENT "First Frame"         '(1 0 100000 1 10 0 1)
		    SF-ADJUSTMENT "Last Frame"          '(10 0 100000 1 10 0 1)
		    SF-TOGGLE     "Make One Image"      TRUE
)

(script-fu-register "script-fu-sequence-save"
		    "<Image>/File/Save Sequence"
		    "Save all layers to numbered sequence of images on disk."
		    "Jaroslav Benkovsky <edheldil@atlas.cz>"
		    "Jaroslav Benkovsky"
		    "July 2000"
		    ""

		    SF-IMAGE      "Image"               0
		    SF-DRAWABLE   "Drawable"            0
		    SF-FILENAME   "File Name Template"  "pict%%.tga"
		    SF-ADJUSTMENT "First Frame"         '(1 1 100000 1 10 0 1)
		    SF-ADJUSTMENT "Last Frame (0: all)" '(0 0 100000 1 10 0 1)
		    SF-TOGGLE     "Preserve size (unimplemented)"  FALSE
		    SF-TOGGLE     "Preserve background" TRUE
)

;; End of file sequence-file.scm

---

### Post by digitalis_vulgaris on 2007-09-21
I manage to insert script-fu in GIMP. But it's not working:

Error: eval: unbound variable: strcspn

I'm working in GIMP 2.3

---

### Post by hikaricore on 2007-09-21
did you install your script via: **gimptool**?

---

### Post by Paul820 on 2007-09-21
Here is another one you could try, i have not tested it so i don't know if it will work.

```
#!/usr/bin/python
#
# Save Layers seperately... Python Fu Script
#
# The plugin extracts the information how to save the layer from it's layer name.
# 
# You can specifiy the image file name to save the layer to by including a space separated
# file name  ending with .gif, .jpg or .png in the layer name
#
# Layers refering to the same file name will be merged.
#
# The plugin also supports specifying the coordinates of the upper left 
# corner in the target image in brackets.
#
# example : "myLayer test.png [64,0]" would copy the layer to the position 64,0 in the 
#           destination image.
#
# Note that GIMP will minimize the resulting image. 
#
import os
import gimp
from gimpfu import *

# layer info class
class layerInfo:
	def __init__(self, name, x, y, filename, offX, offY):
		# full layer name
		self.name=name
		# x coord in the target image
		self.x=x
		# y coord in the target image
		self.y=y
		# filename
		self.filename=filename
		# x offset in the source image
		self.offX=offX
		# y offset in the source image		
		self.offY=offY

# returns a corrected absolute path to a folder
def check_path( path):
	path = os.path.abspath( path)
	if not os.path.exists( path):
		os.mkdir(path)
	if not os.path.isdir( path):
		path = os.path.dirname( path)
	return path

# creates and returns an layerInfo for a given gimp layer
def create_layer_info( layer):
	# split the layer name into space seperated pieces
	for part in layer.name.split( ' '):
		# convert part to lower case
		part=part.lower()
		# do we have a supported web image file?
		if part.endswith('.gif') or part.endswith('.jpg') or part.endswith('.png'):
				# yes -> initialize x,y position and offset
				x=0
				y=0
				offset=pdb.gimp_drawable_offsets( layer)
				# assign filename
				filename=part
				# do we have a [ in the layer name?
				start=layer.name.find("[")
				if start >= 0:		
					# yes, do we have a ] in the layer name?
					end=layer.name.find("]", start)
					if end >=0:
						# yes -> extract first two comma separated values as coordinates
						coords=layer.name[start+1:end].split( ',')
						x=int(coords[0].strip())
						y=int(coords[1].strip())						
				# create and return layerInfo														
				return layerInfo( layer.name, x, y, filename, offset[0], offset[1])
	# return no layerInfo
	return None

# returns the layer with the given name from this list or None
def get_layer_from_list( l, name):
	for layer in l:
		if layer.name == name:
			return layer
	return None

# plugin entry function for our GIMP plugin
def py_saveLayer( image, drawable, save_path):
	# correct destination path
	save_path = check_path( save_path)

	#maps a filename to a list of layers
	names={}
	for curLayer in image.layers:
		# create layer info from layer
		layerInfo=create_layer_info( curLayer)
		# do we have a layer info
		if layerInfo and len(layerInfo.filename) > 0:
			# yes -> create or get list and add layer info to it
			if names.has_key( layerInfo.filename):
				l=names[layerInfo.filename]
			else:
				l=[] 
				names[layerInfo.filename]=l
			# remember layerinfo			
			l.append( layerInfo)
		
	
	# initialize origin (upper left corner) with -1
	origX=-1
	origY=-1
	# for all file names
	for filename in names:	
		full=os.path.join( save_path, filename)
		# duplicate image to tempory image
		tmp=image.duplicate()
		# we don't want GIMP to allocate any undo buffers
		tmp.disable_undo()
		# remove layers whose names do not contain the current file name
		for curLayer in tmp.layers:			
			layerInfo=get_layer_from_list( names[filename], curLayer.name)
			# is there a layer info for the current layer?
			if layerInfo:				
				# yes -> is the origin already set?
				if origX < 0:
					# no -> remember first layer offset in source image as origin
					origX=layerInfo.offX
					origY=layerInfo.offY

				# set offset in target image regarding the specified coordinates and the inter-layer offsets
				curLayer.set_offsets( layerInfo.x+(layerInfo.offX-origX), layerInfo.y+(layerInfo.offY-origY))				
				# ensure layer is visible
				curLayer.visible=1
			else:
				# no layer info -> remove layer from temp image
				tmp.remove_layer( curLayer)
		
		# if we have more than 1 layer, merge visible layers to image size
		if len( tmp.layers) > 1:
			tmp.merge_visible_layers( 0)

		# save temporary image
		pdb.gimp_file_save( tmp, tmp.active_layer, full, full)
		# delete temporary image		
		gimp.delete( tmp)

	# write image info
	info=open( os.path.join( save_path, "image.info"), "w")
	line = "image %dx%d %s\n" % ( image.width, image.height, image.filename.replace(" ", "_"))
	info.write(line)
	for curLayer in image.layers:
		offset=pdb.gimp_drawable_offsets( curLayer)
		line = "layer %dx%d %d,%d %s\n" % ( curLayer.width, curLayer.height,  offset[0], offset[1], curLayer.name.replace(" ", "_"))
		info.write( line)
	info.close()

# GIMP FU register
register(
	"py_saveLayer",
	"Saves the layer as seperate images.",
	"Assign all layers to a target image by putting a file name containing no spaces and ending with .gif, .jpg or .png in the layer name, separated by a space from the rest of the name. Layers refering to the same file name will be merged.",
	"Sven Helmberger",
	"Sven Helmberger",
	"2005",
	"<Image>/File/Save layers seperately...",
	"*",
	[
		(PF_FILE, "save_path", "Path to save the images to", os.getcwd()),
	],
	[],
	py_saveLayer)

main()
```

---

