# graph_matrix
#include<bits/stdc++.h>
using namespace std;
void print_bfs(int *matrix,int n,int st,bool &visited_bfs)
{
	queue<int> pendingnode;
	pendingnode.push(st);
	visited_bfs[st]=true;
	while(pendingnode.size()!=0)
	{
		int current=pendingnode.front();
		pendingnode.pop();
			visited_bfs[st]=true;
		cout<<current<<endl;
		for(int i=0;i<n;i++)
		{
			if(i==current)
			{
				continue;
			}
			if(matrix[current][i]==1&&visited_bfs[i]!=true)
			{
				pendingnode.push(i);
					visited_bfs[i]=true;
			}
		}
	}
}
void print(int *matrix,int n,int st,bool &visited)
{
	cout<<st<<endl;
	visited[st]=true;//visited matrix
	
	for(int i=0;i<n;i++)
	{
		if(matrix[st][i]==1&&visited[i]!=true)
		{
			print(matrix,n,i,visited);
		}
		
	}
}
int main()
{
	int n,e;//n= number of vertrix and e= number of edge
	cin>>n>>e;
	int *matrix=new int[n];//adjacent matrix
	for(int i=0;i<n;i++)
	{
		matrix[i]=new int[n];
		for(int j=0;j<n;j++)
		{
			matrix[i][j]=0;
		}
	}
//	cout<<endl<<"without filling value "<<endl;
//	for(int i=0;i<n;i++)
//	{
//		for(int j=0;j<n;j++)
//		{
//			cout<<matrix[i][j]<<" ";
//		}
//		cout<<endl;
//	}
	
	for(int i=0;i<e;i++)
	{
		int key1,key2;
		cin>>key1>>key2;
		matrix[key1][key2]=1;
		matrix[key2][key1]=1;
	}
	
//		cout<<endl<<"after filling value "<<endl;
//	for(int i=0;i<n;i++)
//	{
//		for(int j=0;j<n;j++)
//		{
//			cout<<matrix[i][j]<<" ";
//		}
//		cout<<endl;
//	}
	
	bool *visited=new bool[n]();
	cout<<endl;
	for(int i=0;i<e;i++)
	  cout<<visited[i]<<" ";
	cout<<endl;
	for(int i=0;i<e;i++){
		if(visited[i]==false){
	cout<<"COMPONENT OF GRAPH according to DFS"<<endl;
     	print(matrix,n,i,visited);
     	cout<<endl;
     }
    }
    //BFS
    bool *visited_bfs=new bool[n]();
    for(int i=0;i<e;i++){
		if(visited_bfs[i]==false){
	cout<<"COMPONENT OF GRAPH according to BFS"<<endl;
     	print_bfs(matrix,n,i,visited_bfs);
     	cout<<endl;
     }
    }
	
}
