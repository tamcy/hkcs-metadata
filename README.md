# Metadata for the *Reference Glyphs for Chinese Computer Systems in Hong Kong*

## Background

The Office of the Government Chief Information Officer (OGCIO) of Hong Kong released the *[Reference Glyphs for Chinese Computer Systems in Hong Kong](https://www.ogcio.gov.hk/en/our_work/business/tech_promotion/ccli/cliac/reference_glyphs.html)* (*Reference Glyphs*) in 2016.

*Reference Glyphs* provides a complete set of Chinese glyphs which covers all the characters in Big-5 and the Hong Kong Supplementary Character Set – 2016. The document includes character forms (glyphs) that are deemed “suitable for application in Hong Kong”. Character forms that are different from the *Standard Typefaces for Chinese Characters* as specified by Taiwan's Ministry of Education (MoE) are also highlighted for clarity.

While the document serves valuable information to font product vendors, its distribution format (one single PDF file) isn't convenient for computer processing. For instance, it is not easy to extract the glyph of a particular code point for inspection. Also querying glyphs that are different from the MoE standard isn't straightforward. This repository serves as a community effort to fill the gap by providing a computer-friendly metadata file which data are derived from *Reference Glyphs*. Ultimately I'd hope the corresponding party to release such information officially.

This is a personal project and is not affiliated with the government. The file is provided “as is”, use it at your own risk.

## Data Format

The file is encoded in JSON. Attributes of the elements are described as follows:

| Name       | Description | 
| ---------- | ----------- |
| codepoint  | Unicode code point
| char       | The corresponding character
| source     | `H`: HKSCS character; `T`: Big5 character 
| big5       | Big-5 code point, or `null` if not applicable <sup>[1](#footnote-big5)</sup>.
| h-source   | H-Source value, or `null` if not applicable <sup>[2](#footnote-hsource)</sup>.
| tw-diff    | If `true`, the specified character form is different from Taiwan MoE's standard, otherwise `false`. This value will be `null` for HKSCS characters.
| page       | The page where this character is located <sup>[3](#footnote-page)</sup>.
| position   | Start and end coordinates of the character in the page `(x1, y1, x2, y2)` <sup>[4](#footnote-coordinates)</sup>.

<a name="footnote-big5">[1]</a>: Obtained from the `Unihan_OtherMappings.txt` file of the [Unihan Database](http://www.unicode.org/versions/components-9.0.0.html).

<a name="footnote-hsource">[2]</a>: The H-Source value is derived from [Hong Kong Supplementary Character Set related information](https://data.gov.hk/tc-data/dataset/hk-ogcio-st_div_01-hong-kong-supplementary-character-set-related-information)

<a name="footnote-page">[3]</a>: Page number is relative to the corresponding section (Table 1: Code Table of Hong Kong Kai Style Character Glyphs / 附表一：香港楷體字形與字碼表 or Table 2: Code Table of Hong Kong Song Style Character Glyphs / 附表二：香港宋體字形與字碼表) of *Reference Glyphs*, not the whole PDF document.

<a name="footnote-coordinates">[4]</a>: This assumes that pages in the PDF document are exported as images in 600dpi (image resolution: 5100×6600px).
