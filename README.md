# svg5.js
A tiny JS library to generate static SVGs for plotters, lasercutting, embroidery and more, based on Processing/p5js syntax.

## Example
```html
<script src="https://ghcdn.rawgit.org/MAKIO135/svg5.js/master/svg5.js"></script>
<script>
    createSVG(windowWidth, windowHeight)
    background('red')
    stroke('black')
    noFill()
    for(let y = -150; y <= height + 150; y += 5){
        beginShape()
        vertex(-10, height + 100)
        for(let x = -10; x <= width + 10; x += 10){
            vertex(x, y + noise(x/500, y/200) * 50)
        }
        vertex(width + 10, height + 100)
        endShape(CLOSE)
    }
</script>
```

## Documentation

- `createSVG(width, height [, parentCSSSelector])`

### Global variables
- `width`: width of the SVG.
- `height`: height of the SVG.
- `CLOSE`: used to specify if a path should be closed.

### Shapes
- `circle(centerX, centerY, radius)`
- `ellipse(centerX, centerY, width, height)`
- `rect(x, y, width, h)`
- `square(x, y, width)`
- `line(x1, y1, x2, y2)`
- `polyline(x1, y1, x2, y2, x3, y3 [, …, xn, yn])`
- `triangle(x1, y1, x2, y2, x3, y3)`
- `quad(x1, y1, x2, y2, x3, y3, x4, y4)`
- `polygon(x1, y1, x2, y2, x3, y3 [, …, xn, yn])`
- `regularPolygon(centerX, centerY, radius [, startAngle])`

### Styling
- `background(color)`
- `clear()`
- `opacity(amount)` where amount goes from 0 to 1.
- `fill(color)`, 
- `noFill()`
- `stroke(color)`
- `strokeWidth(n)` 
- `strokeWeight(n)` alias for `strokeWidth`.
- `strokeCap(style)`
- `strokeJoin(style)`
- `noStroke()`

The `color` parameter for `background`, `fill` and `stroke` functions can be passed either as:
- gray level between 0 (black) and 255 (white): `fill(255)` (white)
- gray and alpha levels between 0 and 255: `fill(255, 100)` (white with alpha)
- red, green and blue levels between 0 and 255: `fill(255, 0, 0)` (red)
- red, green, blue and alpha levels between 0 and 255: `fill(255, 0, 0, 100)` (red with alpha)
- a CSS color string, ie: `fill("red")`, `fill("#ff0000")`, `fill("rgb(255, 0, 0)")`, `fill("rgba(0, 0, 0, 0.5)")`, `fill("hsl(30, 100%, 50%)")`, …

### Vertex shapes
- `beginShape()`
- `vertex(x, y)`
- `bezierVertex(x1, y1, x2, y2, x, y)`
- `cubicVertex(x2, y2, x, y)`
- `quadraticVertex(x1, y1, x, y)`
- `endShape([CLOSE])`

### Math helpers()
- `random()` random(max) or random(min, max)
- `noiseSeed(seed)`
- `noise(x [, y , z , w])` computes a value using simplex noise 1D to 4D.
- `lerp(a, b, t)` calculates value between `a` and `b` at a specific increment between 0 and 1.
- `map(n, start1, end1, start2, end2)` re-maps a number from one range to another.
- `constrain(value, min, max)` constrains a value between a minimum and maximum value.

### Matrix transformations
- `translate(x, y)`
- `rotate(degrees)`
- `scale()` scale(n) for uniform scale or scale(x, y).
- `push()` start a new drawing state.
- `pop()` restore previous state.

### Save SVG file
- `save()`