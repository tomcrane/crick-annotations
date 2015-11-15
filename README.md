# crick-annotations

*Demonstration of transcription annotations for IIIF*

This contrived example demonstrates the following:

* The manifest (wellcome-crick-dna-structure-letter.json) has an annotation that links to a blog post about the letter. This annotation is at the manifest level, not on a canvas.
* Each canvas has an annotation list that provides the text of the page as a single annotation. Clients might render this in a fixed width typeface, preserving the line breaks. This could be rendered alongside the image rather than overlaid. These annotations are "on" the canvas without an xywh fragment selector; a client can't paint them directly at a particular region, they annotate the canvas as a whole.
* Page 3 has a line by line transcription annotation list as well. These annotations each have an xywh fragment selector, so can be painted on directly. Crick's handwriting doesn't keep to a straight line, so the rectangles are larger than we might want and clip the lines above and below. We could use an SVG fragment selector to draw a parallelogram (or any shape) but let's keep it simple for clients for now.
* Page 3 has a third annotation list providing commentary. The commentary annotation list (p3-commentary.json) demonstrates annotating a region (in this case Crick's diagram) with a couple of images, and also a comment on a sentence from the text.

This manifest has all the above:

[wellcome-crick-dna-structure-letter.json]

This manifest (which works in Mirador's transcriptions branch) only includes the page 3 transcription annotations, which all have xywh fragment selectors.

[wellcome-crick-dna-structure-letter-mirador.json]

TODO: provide another commentary annotation list that is NOT declared in the manifest. In this case the user has walked up to the manifest with an annotation list it doesn't know about; a viewer needs to allow a user to load an annotation list from an arbitrary URL or from the local file system (the latter may need assistance from an annotation server to expose the list at a URL).
