<pre># aggregation_framework_assign_medium


1. db.products.aggregate([
  {
		$group:{
			_id:"$supplier.name",
			totalQuantity: {$sum:"$quantity"}
}
}
])

<img width="163" alt="image" src="https://github.com/user-attachments/assets/70746235-5c7e-47e8-ab3a-8127327a1dfd" />
<img width="152" alt="image" src="https://github.com/user-attachments/assets/adbfe636-0741-4ef6-856c-634df17b0b3f" />



{
  _id: 'FashionHub',
  totalQuantity: 280
}
{
  _id: 'ActiveLife',
  totalQuantity: 90
}
{
  _id: 'SoundWave',
  totalQuantity: 60
}
{
  _id: 'TechGlobe',
  totalQuantity: 60
}
{
  _id: 'GadgetPro',
  totalQuantity: 125
}
{
  _id: 'HomeBest',
  totalQuantity: 30
}
{
  _id: 'StyleCraft',
  totalQuantity: 120
}
2. db.products.aggregate([
  {
	$unwind : "$tags"
},
  {
$group:{
_id:"$tags",
averagePrice:{$avg:"$price"}
}
},
  {
$sort: {
averagePrice: -1
}
}
])



{
  _id: 'work',
  averagePrice: 1200
}
{
  _id: 'portable',
  averagePrice: 493
}
{
  _id: 'computer',
  averagePrice: 433.3333333333333
}
{
  _id: 'kitchen',
  averagePrice: 250
}
{
  _id: 'appliance',
  averagePrice: 250
}
{
  _id: 'coffee',
  averagePrice: 250
}
{
  _id: 'gadget',
  averagePrice: 199
}
{
  _id: 'wearable',
  averagePrice: 199
}
{
  _id: 'audio',
  averagePrice: 80
}
{
  _id: 'mechanical',
  averagePrice: 75
}
{
  _id: 'denim',
  averagePrice: 60
}
{
  _id: 'wireless',
  averagePrice: 52.5
}
{
  _id: 'peripheral',
  averagePrice: 50
}
{
  _id: 'fashion',
  averagePrice: 45
}
{
  _id: 'leather',
  averagePrice: 45
}
{
  _id: 'clothing',
  averagePrice: 40
}
{
  _id: 'fitness',
  averagePrice: 30
}
{
  _id: 'exercise',
  averagePrice: 30
}
{
  _id: 'cotton',
  averagePrice: 20
}
{
  _id: 'casual',
  averagePrice: 20
}
3. db.products.aggregate([
  {
$match:{
date_added:{
$gte: new Date("2023-02-01T00:00:00Z"),
$lt:new Date("2023-03-01T00:00:00Z")
}
}
},
  {
$project:{
_id:0,
name:1,
category : 1,
formattedDateAdded:{
$dateToString:{format:"%Y-%m-%d",date:"$date_added"}
}
}
}
])

<img width="229" alt="image" src="https://github.com/user-attachments/assets/fcab1498-46a4-4f5b-88f6-aed72ed2ccd4" />


{
  name: 'Wireless Mouse',
  category: 'Electronics',
  formattedDateAdded: '2023-02-01'
}
{
  name: 'Espresso Machine',
  category: 'Home Goods',
  formattedDateAdded: '2023-02-15'
}
{
  name: 'Bluetooth Speaker',
  category: 'Electronics',
  formattedDateAdded: '2023-02-25'
}
aggregationAssignmentDB
Selection deleted

</pre>
