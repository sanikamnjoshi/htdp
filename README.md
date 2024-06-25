# htdp
Me following along with Gregor Kiczales' edX course on HtDP.

# notes
*I am including any notes I make in this README. because why not.*

## design recipes

### htdf (functions)
1. signature, purpose and stub
2. define examples, wrap each in `check-expect`
3. template and inventory
4. code the function body
5. test and debug until correct

### htdd (data)
first identify form of information, then write:
1. a possible structure definition (not until compound data)
2. a type comment that defines type name and describes how to form data
3. an interpretation to describe correspondence between information and data
4. one or more examples of the data
5. a template for a 1 argument function operating on data of this type

> [!info] test guidelines
> 1. at least 2
> 2. different argument/field values
> 3. code coverage
> 4. points of variation in behavior
> 5. 2 long / 2 deep

### htdw (worlds)
1. domain analysis (use a piece of paper!)
	1. sketch program scenarios
	2. identify constant information
	3. identify changing information
	4. identify big-bang options
2. build the actual program
	1. constants (based on 1.2 above)
	2. data definitions (based on 1.3 above)
	3. functions
		1. main first (based on 1.4 and 2.2 above)
		2. wish list entries for big-bang handlers
	4. work through wish list until done

```scheme
(require spd/tags)
(require 2htdp/image)
(require 2htdp/universe)

;; my world program (make this more specific)
(@htdw WS)
;; --------------------------------------------------------------------------------

;; constants:
;; --------------------------------------------------------------------------------

;; data definitions:
(@htdd WS)
;; WS is ... (give WS a better name)
;; --------------------------------------------------------------------------------

;; functions:
(@htdf main)
(@signature WS -> WS)
;; start the world with (main ...)
;;
(@template htdw-main)
(define (main ws)
	(big-bang ws ; WS
		(on-tick tock) ; WS -> WS
		(to-draw render) ; WS -> Image
		(stop-when ...) ; WS -> Boolean
		(on-mouse ...) ; WS Integer Integer MouseEvent -> WS
		(on-key ...) ; WS KeyEvent -> WS
	)
)

(@htdf tock)
(@signature WS -> WS)
;; produce the next ...
;; !!!
(define (tock ws) ws)

(@htdf render)
(@signature WS -> Image)
;; render ...
;; !!!
(define (render ws) empty-image)
;; --------------------------------------------------------------------------------
```
